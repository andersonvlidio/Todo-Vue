<script >
import {XIcon, RefreshIcon} from '@heroicons/vue/outline'
export default {
 emits: ["de-render", "revalidate"],
 props: ['item'],
  methods: {
    async updateItem() {
      const data = { title: this.item.title, description: this.item.description, completed: false }
      await fetch(`https://vue-todo-tasks.herokuapp.com/api/tasks/${this.item.id}`, {
        method: "PUT",
        body: JSON.stringify(data),
        headers: {
          "Content-Type": "application/json"
        }
      })
    this.$emit("revalidate")
    this.$emit("de-render")
    }
  },
  components: { 
    XIcon,
    RefreshIcon
  }
}
</script>

<template>
    <div class="main-modal">
        <div class="show-modal">
            <div class="container-input">
                <div class="element-header">
                    <input 
                    class="input-modal"
                    type="text" 
                    placeholder="Qual o título?"
                    v-model="item.title"
                    />
                    <button class="button-modal close" @click="$emit('de-render')"> <XIcon /> </button>
                </div>
                <textarea 
                    class="input-modal"
                    type="textarea" 
                    placeholder="tem descrição?"
                    v-model="item.description"
                />
            </div>
            <div class="container-button">
                
                <button class="button-modal update" @click="updateItem()"> <RefreshIcon /> </button>
            </div> 
        </div>
    </div>
    
  
</template>

<style scoped>
    .main-modal{
        width: 100%;
        height: 100%;
        background-color: rgba(0,0,0,0.4);
        position: fixed;
        top:0;
        left:0;
        z-index: 2;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .show-modal{
        width: 30%;
        background-color: #fff;
        display: block;
        align-items: center;
        justify-content: center;
        border-radius: 0.5rem;
    }
    .element-header{
        display: flex;
        justify-content: space-between;
    }
    .container-input{
        display: block;
        width: 100%;
    }
    .input-modal {
        all : unset;
        width: 100%;
        background-color: #fff;
        border: none;
        border-style: none;
        color: black;
        padding: 16px 0;
        text-decoration: none;
        margin: 4px 0;
        text-align: left
    }
    .input-modal::placeholder {
        font-weight: 700;
        font-size: 26px
    }
    .container-button{
        display: flex;
        justify-content: flex-end;
        margin-right: 5px;
    }
    .button-modal{
        all: unset;
        height: 30px;
        width: 30px;
        margin: 5px;
        cursor: pointer;
        margin: 8px;
    }
    .close:hover{
    color:#d42c2c;
    }
    .update:hover{
        color: #084510;
    }

</style>
