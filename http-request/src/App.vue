<template>
  <div id="container">
    <div class="row">
      <div class="col-md-8 offset-md-2 text-center">
        <h3 class="mt-5">todo list | vue.js</h3>
        <hr>
        <div class="row">
          <div class="col-md-6 offset-md-3 d-flex flex-row justify-content-between align-items-center">
            <input type="text" v-model="todoText">
            <button @click="addTodo()" class="btn btn-primary">ekle</button>
          </div>
        </div>
        <hr>
        <div class="todo-container">
          <Todo v-for="todo in todoList" :key="todo" />
        </div>
      </div> 

    </div>
  </div>
</template>

<script>

  import Todo from "@/components/Todo"
  import axios from "axios"
export default {
  components : {
    Todo
  },
  data(){
    return {
      todoText : "",
      todoList : [],
    }
  },
  methods: {
    addTodo(){
      // alert("x")
      //axios.post(gideceği url, {verimiz})
      axios.post("https://videoda-vue-b96b8.firebaseio.com/todoList.json", {text : this.todoText})
        .then(response => {
          console.log(response)
        })
        .catch(e => {
          console.log(e)
        })
    }
  },
}
</script>
