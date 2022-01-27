<script >
import Modal from './Modal.vue'

export default {
 data: () => ({
    visible: false
  }),
  methods: {
    toggleModal () {
      this.visible = !this.visible
    }
  },
  components: {
    Modal
  }
}
</script>

<template>
    <Modal v-if="visible" @de-render="toggleModal" @revalidate="$emit('revalidate')" />
    <div class= "header">
      <h1> Qual a de hoje? </h1>
      <button class="new-task" @click="toggleModal"> Nova Tarefa </button>
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
  background-color: #006400;
  color: #fff;
  border-radius: 0.5rem;
  cursor: pointer;
  padding: 8px 16px;
  height: 26px;
}
.new-task:hover {
  box-shadow: 8px 9px 30px -4px #006435;
  transition-duration: .3s;
}
</style>
