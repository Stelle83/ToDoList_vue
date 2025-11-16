<script setup>

import {ref} from "vue";
import {uid} from "uid";
import TodoCreator from "@/components/TodoCreator.vue";

const todoList = ref([]);

const createTodo = (todo) => {
    todoList.value.push({
        id: uid(),
        todo,
        isCompleted: null,
        isEditing: null,
    });
};

</script>

<template>
    <main>
        <h1> Create Todo:</h1>
        <TodoCreator @create-todo="createTodo()"/>

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