<template>
  <div class="input_elem">
    <input @keyup.enter="handleKeyUp" />
  </div>
</template>

<script>
export default {
  methods: {
    handleKeyUp(event) {
      this.$emit('addTodo', event.target.value);
      event.target.value = ''; 
    }
  }
};
</script>

<style scoped>
.input_elem {
  display: flex;
  justify-content: center;
  margin: 20px;
}

.input_elem > input {
  outline: 2px solid black;
  box-shadow: 5px 5px 10px black;
}
</style>
