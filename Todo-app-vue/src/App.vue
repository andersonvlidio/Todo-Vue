<script>
import CardItems from './components/CardItems.vue'
import Header from './components/Header.vue'

export default {
 data: () => ({
   items: [],
    title: '',
    description: '',
    completed: false
  }),
  methods: {
    async reRender () {
      const response = await fetch('https://vue-todo-tasks.herokuapp.com/api/tasks');
      const data = await response.json();
      this.items = data
    }
  },
  async created() {
      const response = await fetch('https://vue-todo-tasks.herokuapp.com/api/tasks');
      const data = await response.json();
      this.items = data
    },
  components: {
    Header,
    CardItems
  }
}
</script>

<template>
  <div class="main-app">
    <Header @revalidate="reRender"/>
    <CardItems @revalidate="reRender" :items="items" />
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
