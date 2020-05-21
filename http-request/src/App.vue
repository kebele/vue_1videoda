<template>
  <div id="container">
    <div class="row">
      <div class="col-md-8 offset-md-2 text-center">
        <h3 class="mt-5">todo list | vue.js</h3>
        <hr>
        <div class="row">
          <div class="col-md-6 offset-md-3 d-flex flex-row justify-content-between align-items-center">
            <input type="text">
            <button class="btn btn-primary">ekle</button>
          </div>
        </div>
        <hr>
        <div class="todo-container">
          <Todo />
        </div>
      </div>

    </div>
  </div>
</template>

<script>

  import Todo from "@/components/Todo"
export default {
  components : {
    Todo
  },
  data(){
    return {

    }
  }
}
</script>
