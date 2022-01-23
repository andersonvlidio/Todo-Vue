<script >

export default {
 emits: ["de-render"],
 data: () => ({
    title: '',
    description: ''
  })
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
                />
                <textarea 
                    class="input-modal"
                    type="textarea" 
                    placeholder="tem descrição?"
                />
            </div>
            <div class="container-button">
                <button class="button-modal " @click="$emit('de-render')"> x </button>
                <button class="button-modal"> C </button>
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
        z-index: 2;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .show-modal{
        width: 50%;
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
