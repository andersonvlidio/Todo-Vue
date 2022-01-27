<script >

export default {
 emits: ["de-render", "revalidate"],
 data: () => ({
    title: '',
    description: '',
    completed: false
  }),
  methods: {
    async saveNewTask(title, description) {
      const data = { title, description, completed: false }
      await fetch('https://vue-todo-tasks.herokuapp.com/api/tasks', {
        method: "POST",
        body: JSON.stringify(data),
        headers: {
          "Content-Type": "application/json"
        }
      })
    this.$emit("revalidate")
    this.$emit("de-render")
    }
  }
}
</script>

<template>
    <div class="main-modal">
        <div class="show-modal">
            <div class="container-input">
                <input 
                    class="input-modal"
                    type="text" 
                    placeholder="Qual o título?"
                    v-model="title"
                />
                <textarea 
                    class="input-modal"
                    type="textarea" 
                    placeholder="tem descrição?"
                    v-model="description"
                />
            </div>
            <div class="container-button">
                <button class="button-modal " @click="$emit('de-render')"> x </button>
                <button class="button-modal" @click="saveNewTask(title, description)"> C </button>
            </div> 
        </div>
    </div>
    
  
</template>

<style>
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
    }
    .button-modal{
        margin: 8px;
    }

</style>
