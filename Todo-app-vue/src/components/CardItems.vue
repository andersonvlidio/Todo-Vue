<script >
  export default {
    props: ['items'],
    emits: ["revalidate"],
    methods: {
      async deleteItem(item) {
        await fetch(`https://vue-todo-tasks.herokuapp.com/api/tasks/${item.id}`, {
          method: 'DELETE',
          headers: {
            'Content-Type': 'application/json',
          }
        })
        this.$emit("revalidate")
      }
    }
  }
</script>

<template>
  <div class="container-card">
    <div class="card" v-for="(item, index) in items" :key="index">
        <div class="container-title">
          <h1>{{item.title}}</h1>
          </div>
        <div class="container-description">
          <h3>{{item.description}}</h3>
        </div>
        <button class="delete" @click="deleteItem(item)">Lixo</button>
        <button class="edit" >Editar</button>
      </div>
     
  </div>
</template>

<style scoped>
.container-card{
  width: 100%;
  display: flex;
  flex-wrap: wrap
}
.card {
  background-color: #fff;
  width: 220px;
  min-height: 200px;
  margin: 18px;
}

</style>
