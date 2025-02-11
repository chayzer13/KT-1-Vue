<template>
    <div
      class="todo_card"
      :style="{ backgroundColor: completed ? 'green' : 'red' }"
      @dblclick="handleDoubleClick"
      @click="handleClick"
    >
      <h2>{{ title }}</h2>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      id: Number,
      title: String,
      completed: Boolean
    },
    methods: {
      handleDoubleClick() {
        this.$emit('deleteTodoByid', this.id);
      },
      handleClick() {
        this.$emit('changeTodos', this.id);
      }
    }
  };
  </script>
  
  <style scoped>
  .todo_card {
    display: flex;
    flex-direction: column;
    padding: 10px;
    margin: 20px 170px;
    outline: 2px solid black;
    box-shadow: 5px 5px 10px black;
  }
  </style>
  