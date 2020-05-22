<template>
  <div id="container">
    <div class="row">
      <div class="col-md-8 offset-md-2 text-center">
        <h3 class="mt-5">todo list | vue.js</h3>
        <hr />
        <div class="row">
          <div
            class="col-md-6 offset-md-3 d-flex flex-row justify-content-between align-items-center"
          >
            <input type="text" v-model="todoText" />
            <button @click="addTodo()" class="btn btn-primary">ekle</button>
          </div>
        </div>
        <hr />
        <div class="todo-container">
          <Todo
            @deleteTodo="deleteTodo($event)"
            v-for="todo in todoList"
            :todo="todo"
            :key="todo.id"
          />
        </div>
      </div>
    </div>
    <!-- <button @click="fetchData">verileri getir</button> -->
  </div>
</template>

<script>
import Todo from "@/components/Todo";
import axios from "axios";
export default {
  components: {
    Todo,
  },
  data() {
    return {
      todoText: "",
      todoList: [],
    };
  },
  methods: {
    addTodo() {
      // alert("x")
      //axios.post(gideceği url, {verimiz})
      axios
        .post("https://videoda-vue-b96b8.firebaseio.com/todoList.json", {
          text: this.todoText,
        })
        .then((response) => {
          console.log(response.data.name);
          this.todoList.push({
            id: response.data.name,
            text: this.todoText,
          });
          console.log(this.todoList);
        })
        .catch((e) => {
          console.log(e);
        });
    },
    deleteTodo(todoId) {
      // alert(todoId); //problem yok id leri alıyor
      axios
        .delete(
          "https://videoda-vue-b96b8.firebaseio.com/todoList/" +
            todoId +
            ".json"
        )
        .then((response) => {
          console.log(response);
          let index = this.todoList.findIndex((i) => {
            return i.id == todoId;
          });
          console.log(index);
          this.todoList.splice(index, 1);
        })
        .catch((e) => {
          console.log(e);
        });
    },
  },
  created() {
    axios
      .get("https://videoda-vue-b96b8.firebaseio.com/todoList.json")
      .then((response) => {
        // console.log(response)
        console.log(response.data);
        for (let key in response.data) {
          console.log(response.data[key]);
          //verileri object olarak aldık
          let todo = {
            text: response.data[key].text,
            id: key,
          };
          // this.todoList.push(response.data[key]);
          console.log(todo.text);
          console.log(todo.id);
          this.todoList.push(todo);
        }
        console.log(this.todoList);
      })
      .catch();
  },
};
</script>
