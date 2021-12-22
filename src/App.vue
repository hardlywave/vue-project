<template>
  <div id="app">
    <TodoCreate
        @create-task = "createTask"
        :todos="todos"
    />
    <hr>
    <h2>To Do List</h2>
    <hr>
    <TodoList
        :todos="todos"
        @remove-todo = "removeTodo"
    />
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import TodoCreate from '@/components/TodoCreate'

export default {

  name: 'App',
  data() {
    return{
      todos: [
        {id: 0, title: 'Купить пиво', complete: false},
        {id: 1, title: 'Купить ром', complete: false},
        {id: 2, title: 'Купить виски', complete: false},
        {id: 3, title: 'Купить мясо', complete: false}
      ],
    }
  },
  components: {
    TodoList,
    TodoCreate
  },
  methods: {
    removeTodo(id){
      this.todos = this.todos.filter(t => t.id !== id)
    },
    createTask(Task){
      this.todos.push(Task)
      // this.todos.id = this.todos.length + 1;
    },
  }
}
</script>

<style>
  body {
    background-color: orange;
    overflow: hidden;
    position: relative;
    text-align: center;
  }
  #app {
    background-color: white;
    width: 750px;
    height: 750px;
    border: 2px solid ;
    border-radius: 12%;
    display: inline-block;
    position: relative;
  }
  hr {
    margin: 20px 0;
    padding: 0;
    height: 10px;
    border: none;
    border-top: 1px solid #333;
    box-shadow: 0 10px 10px -10px #8c8b8b inset;
  }
  h2{
    text-align: center;
    font-style: italic;
  }

</style>
