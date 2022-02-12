<script >
  import { TrashIcon, PencilAltIcon } from '@heroicons/vue/outline'
  export default {
    props: ['items'],
    emits: ["revalidate", "render", "edit-todo"],
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
    },
    components: { 
      TrashIcon, 
      PencilAltIcon
    }
  }
</script>

<template>
  <div class="container-card">
    <div class="card" v-for="(item, index) in items" :key="index" @click="$emit('render', item)" >
      <div class="container-title">
        <h1>{{item.title}}</h1>
      </div>
      <div class="container-description">
        <p>{{item.description}}</p>
      </div>
      <div class="container-button">
        <button class="delete cart-button" @click="deleteItem(item)"> <TrashIcon class="h-3 w-3"/></button>
      </div>
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
  border-radius: 1.6rem;
  width: 28%;
  margin: 18px;
  box-shadow: 0px 5px 15px -7px #000;
  cursor: pointer;
}
.card:hover{
  box-shadow: 0 0 8px #d3d3d3;
}
.container-description{
  height: auto;
  margin: 50px 0;
  max-height: 100%;
}

.container-description p, 
.container-title h1{
  word-wrap: break-word

}
.container-button{
  margin-right: 5px;
  text-align: end;
}
.cart-button{
  all: unset;
  height: 30px;
  width: 30px;
  margin: 5px;
  cursor: pointer;
}
.delete:hover{
  color:#d42c2c;
}
</style>
