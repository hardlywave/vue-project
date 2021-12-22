<template>
  <li>
    <span>
       <strong>{{todo.id+1}}:</strong>
       {{todo.title}}
    </span>
    <div class="div-buttons">
      <button class="item-delButton"
            v-on:click="$emit('remove-todo', todo.id)"
    >&times;</button>
    </div>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    },
    index: Number,
  },
}
</script>

<style scoped>
  li {
    display: flex;
    border: 2px solid #008CBA;
    border-radius: 5px;
    justify-content: space-between;
    margin: .5rem;
    padding: .5rem 2rem;
    width: 400px;
    background-color: transparent;
  }

  span {
    font: 16px "Trebuchet MS", "Lucida Sans";
    justify-content: center;
  }
  .item-delButton {
    background: rgba(203, 0, 0, 0.99);
    color: #fff;
    border-color: transparent;
    border-radius: 50%;
    font-weight: bold;
    margin: 0 5px;
    right: 0;
  }
  {/* Green Button for li */

  /*.item-addButton {*/
  /*  background: #4CAF50;*/
  /*  color: #fff;*/
  /*  border-color: transparent;*/
  /*  border-radius: 50%;*/
  /*  font-weight: bold;*/
  /*  margin: 0 5px;*/
  /*  right: 0;*/
  /*}*/}
  .div-buttons {
    position: relative;
    justify-content: space-evenly;
  }

</style>