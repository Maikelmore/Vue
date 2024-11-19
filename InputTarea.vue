<script setup>

    import {ref} from 'vue';

    const sNuevoPostTitulo=ref("");
    const sNuevoPostCuerpo=ref("");

    const emit = defineEmits(["agregarTarea"]);

    function emitirNuevaTarea() {

        // Emite el emit si los dos campos tienen texto

        if(sNuevoPostTitulo.value.trim() != "" && sNuevoPostCuerpo.value.trim() != ""){

            emit("agregarTarea", sNuevoPostTitulo.value, sNuevoPostCuerpo.value);
            sNuevoPostTitulo.value = "";
            sNuevoPostCuerpo.value = "";

  
        }else {
            alert("Por favor, completa ambos campos.");
        }
    }

</script>


<template>

    
    <div class="nuevo-post-form">

        <h3>Introduce texto y agrega</h3>

        <input type="text" v-model="sNuevoPostTitulo" placeholder="Titulo del post" />

        <textarea type="text" v-model="sNuevoPostCuerpo" placeholder="Cuerpo del post"></textarea>

        <button @click="emitirNuevaTarea">Agregar</button>

    </div>

</template>


<style scoped>
    
    .nuevo-post-form{
        margin-bottom: 30px;
        max-width: 600px;
        display: flex;
        flex-direction: column;
    }

    .nuevo-post-form input,
    .nuevo-post-form textarea{
        width: 100%;
        padding: 10px;
        margin-bottom: 10px;
        border: 2px solid #ddd;
        border-radius: 5px;
        font-size: 1rem;
        transition: border-color 0.3s;


    }

    .nuevo-post-form button {
    padding: 10px 20px;
    border: none;
    background-color: #4c1aff;
    color: white;
    font-size: 1rem;
    border-radius: 5px;
    cursor: pointer;
    }


    .nuevo-post-form button:hover{
        background-color: #4c1aff;
        transform: scale(1.05);

    }

    .nuevo-post-form input:focus,
    .nuevo-post-form textarea:focus {
    border-color: #4c1aff;
    outline: none;
    }
</style>
