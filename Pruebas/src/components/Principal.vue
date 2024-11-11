<script setup>
    import { defineProps } from 'vue';
     const props=defineProps({
        sTitulo:{
            type:String,
            default:'Titulo de tu app'
        }
    });


</script>

<template>
    <h1> {{sTitulo}} </h1>
 
</template>

<style scoped>


</style>