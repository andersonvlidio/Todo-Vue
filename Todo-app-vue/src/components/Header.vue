<script >
  export default {
    emits: ["render"]
  }
</script>

<template>
  <div class= "header">
    <h1> what's up today?</h1>
    <button class="new-task" @click="$emit('render')"> New task </button>
  </div>
</template>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  padding: 32px 0;
  align-items: center;
  margin: 0 0 32px;
  width: 768px;
}
.new-task {
  all : unset;
  background-color: #084510;
  color: #fff;
  border: 1px solid #084510;
  border-radius: 0.5rem;
  cursor: pointer;
  padding: 8px 16px;
  height: 26px;
}
.new-task:hover {
  background-color: rgb(241 245 249);
  color: #084510;
  transition-duration: 0.5s;
}
</style>
