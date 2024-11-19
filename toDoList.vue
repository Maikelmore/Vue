<script setup>

    import {ref} from 'vue';
    import InputTarea from "./InputTarea.vue";
    
    const posts = ref([

        // Tarea de muestra para servir de base para añadir IDs, etc
        {id:1, titulo:"Tarea 1", cuerpo: "Tarea de muestra", completada: false},

    ]);


    function agregarNuevoPost(sNuevoPostTitulo, sNuevoPostCuerpo) {
        const iIdNuevo=posts.value.length+1;
        posts.value.push({id:iIdNuevo, titulo:sNuevoPostTitulo, cuerpo: sNuevoPostCuerpo, completada: false});
    }

    function tareaCompletada(id) {
        const tarea = posts.value.find(post => post.id === id);
        if (tarea){
            tarea.completada = !tarea.completada;
        }
    }

    function eliminarTarea(id) {
        posts.value = posts.value.filter(post => post.id !== id); // Filtra la tarea con el id especificado
    }

</script>


<template>

    <InputTarea @agregarTarea="agregarNuevoPost" />

    <div class="contenedor-posts">

        <h4>Pulsa en una tarea para completarla</h4>

        <div v-for="post in posts" :key="post.id" class="post" @click="tareaCompletada(post.id)">

            <h2 :class = "{completada: post.completada}" > {{ post.titulo }} </h2>
            <p :class = "{completada: post.completada}" > {{ post.cuerpo }} </p> 
            <button @click.stop="eliminarTarea(post.id)">Eliminar</button> <!-- El .stop permite que la tarea no se marque como completada al clickar en Eliminar -->

        </div>

    </div>

</template>


<style scoped>

    .contenedor-posts{

        flex-direction: column;
        align-items:flex-start;
        padding: 20px;
        border-radius: 10px;
        max-width: 800px;
        width: 100%;
    }

    .post{

        margin-bottom: 20px;
        padding: 15px;
        border: 2px solid #ccc;
        border-radius: 10px;
    }

    /* Esto permite que el texto no se desborde, y se mantenga dentro del contenedor */
    
    .post p{    

        white-space: normal;
        word-wrap: break-word;
    }

    .post:hover{
        transform: translateY(-5px);
        box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
    }

    .completada{
        text-decoration: line-through;
        color: grey;
    }
    
    button{
        margin-top: 8px;
        border: none;
        padding: 5px;
        background-color: #4c1aff;
        color: white;
        border-radius: 2px;
        cursor: pointer;
    }
</style>
