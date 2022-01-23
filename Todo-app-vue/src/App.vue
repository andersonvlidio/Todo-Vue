<script setup>
import HelloWorld from './components/HelloWorld.vue'
import Header from './components/Header.vue'

</script>

<template>
  <div class="main-app">
    <Header/>
    <HelloWorld msg="Hello Vue 3 + Vite" />
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

#app {
  font-family: 'Roboto', sans-serif;;
  display: flex;
  justify-content: center;
  text-align: center;
  color: #2c3e50;
  background-color: rgb(241 245 249);
  min-height: 100vh
}
.main-app{
  max-width: 768px;
}
</style>
