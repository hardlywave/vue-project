<template>
  <div>
    <ul>
      <TodoItem
          v-for="todo in todos" :key="todo.id"
          :todo="todo"
          v-on:remove-todo="removeTodo"
      />
    </ul>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem'

export default {
  props: ['todos'],
  components: {
    TodoItem
  },
  methods: {
    removeTodo(id){
      this.$emit('remove-todo', id)
    }
  }
}
</script>

<style scoped>
  div {
    text-align: center;
    background-color: transparent;
  }
  ul {
    display: inline-block;
    list-style: none;
    margin: 0;
    padding: 0;
    position: relative;
  }
</style>