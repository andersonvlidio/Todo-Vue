<script>
import CardItems from './components/CardItems.vue'
import Header from './components/Header.vue'
import Modal from './components/Modal.vue'
import ModalUpdate from './components/ModalUpdate.vue';

export default {
 data: () => ({
   items: [],
   visible: false,
   updateModalVisible: false,
   editTodo: null
  }),
  methods: {
    async reRender () {
      const response = await fetch('https://vue-todo-tasks.herokuapp.com/api/tasks');
      const data = await response.json();
      this.items = data
    },
    toggleModal () {
    this.visible = !this.visible
    },
    toggleUpdateModal () {
      this.updateModalVisible = !this.updateModalVisible
    },
    handleUpdateTask(item){
      this.editTodo = item
      this.toggleUpdateModal()
    }
  },
  async created() {
      const response = await fetch('https://vue-todo-tasks.herokuapp.com/api/tasks');
      const data = await response.json();
      this.items = data
  },
  components: {
    Header,
    CardItems,
    Modal,
    ModalUpdate
}
}
</script>

<template>
  <div class="main-app">
    <ModalUpdate v-if="updateModalVisible" @revalidate="reRender" @de-render="toggleUpdateModal" :item="editTodo" />
    <Modal v-if="visible" @de-render="toggleModal" @revalidate="reRender" :items="items"/>
    <Header @render="toggleModal" />
    <CardItems @render="handleUpdateTask" @revalidate="reRender" :items="items" />
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

#app {
  font-family: 'Roboto', sans-serif;
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
