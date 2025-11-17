<script setup>
import {ref} from "vue";
import {uid} from "uid";
import { Icon } from "@iconify/vue";
import TodoCreator from "@/components/TodoCreator.vue";
import TodoItem from "@/components/TodoItem.vue";

const todoList = ref([]);

const fetchTodoList = () => {
    const savedTodoList = JSON.parse(localStorage.getItem("todoList"));
    if (savedTodoList) {
        todoList.value = savedTodoList;
    }
};

fetchTodoList();

const setTodoListLocalStorage = () => {
    localStorage.setItem("todoList", JSON.stringify(todoList.value));
};

const createTodo = (todo) => {
    todoList.value.push({
        id: uid(),
        todo,
        isCompleted: null,
        isEditing: null,
    });
    setTodoListLocalStorage();
};

const toggleTodoComplete = (todoPos) => {
    todoList.value[todoPos].isCompleted = !todoList.value[todoPos].isCompleted;
    setTodoListLocalStorage();
};

const toggleEditTodo = (todoPos) => {
    todoList.value[todoPos].isEditing = !todoList.value[todoPos].isEditing;
    setTodoListLocalStorage();
};

const updateTodo = (todoVal, todoPos) => {
    todoList.value[todoPos].todo = todoVal;
    setTodoListLocalStorage();
};

const deleteTodo = (todoId) => {
    todoList.value = todoList.value.filter((todo) => todo.id !== todoId);
    setTodoListLocalStorage();
};
</script>

<template>
    <main>
        <h1> Create Todo:</h1>
        <TodoCreator @create-todo="createTodo"/>
        <ul class="todo-list" v-if="todoList.length > 0">
            <TodoItem
                v-for="(todo, index) in todoList" 
                :todo="todo" 
                :index="index" 
                @toggle-complete="toggleTodoComplete"
                @edit-todo="toggleEditTodo"
                @update-todo="updateTodo"
                @delete-todo="deleteTodo"
            />
        </ul>
        <p class="todos-msg" v-else>
            <span>Are you sure you have nothing to do?</span>
            <Icon icon="noto:thinking-face" width="22" />
        </p>
    </main>
</template>

<style scoped>
    h1 {
        margin-bottom: 16px;
        text-align: center;
    }

        .todo-list {
            display: flex;
            flex-direction: column;
            list-style: none;
            margin-top: 0;
            padding: 24px;
            gap: 20px;
        }

    .todos-msg {
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 8px;
        margin-top: 24px;
    }


    main {
        display : flex;
        flex-direction: column;
        max-width: 500px;
        margin: 0 auto;
        padding: 40px 16px;
    }
</style>