<script setup>
import TodoCreator from "@/components/TodoCreator.vue";
   
</script>

<template>
    <main>
        <h1> Create Todo:</h1>
        <TodoCreator/>
        
    </main>
</template>

<style scoped>
    h1 {
        color: blue;
        margin-bottom: 16px;
        text-align: center;
    }

    main {
        display : flex;
        flex-direction: column;
        max-width: 500px;
        margin: 0 auto;
        padding: 40px 16px;
    }
</style>