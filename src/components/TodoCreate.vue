<template>
  <div class="main">
    <h2>Creating Task</h2>
    <hr>
    <form @submit.prevent="onsubmit">
      <div class="in-div">
        <label>Task name</label>
        <input v-model="title" placeholder="Enter your task">
      </div>
      <button type="submit">Add task</button>
    </form>
  </div>
</template>

<script>
export default {
  props: {
    todos:{
      type: Array,
      required: true,
    }
  },
  data() {
    return{
      title: '',
    }
  },

  methods: {
    onsubmit(){
      try{
        let obj = JSON.parse(JSON.stringify(this.todos));
        if(this.title.trim()){
          if(obj.length <= 6){
            const newTask = {
              id: obj.length,
              title: this.title,
              complete: false
            }
            this.$emit('create-task', newTask)
            this.title = null;
          }else{
            alert("List is full");
          }
        } else {
          alert("Task name is empty")
        }
      } catch (e){
        alert("Task name is empty")
      }
    }
  }
}
</script>
<style scoped>
  h2 {
    text-align: center;
    font-style: italic;
  }

  label {
    text-align: start;
    font-style: italic;
  }

  form {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  input {
    width: 400px;
    height: 25px;
    border: 2px solid #008CBA;
    border-radius: 5px;
  }

  button {
    width: 150px;
    background-color: #4CAF50; /* Green */
    border-radius: 5%;
    border-color: transparent;
    color: white;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    font-size: 16px;
    margin: 20px 0;
  }
  .main {
    background-color: transparent;
    position: relative;
  }
  .in-div {
    display: flex;
    flex-direction: column;
  }
</style>