<script setup>
import {ref, watch, computed} from "vue";
import {uid} from "uid";
import { Icon } from "@iconify/vue";
import TodoForm from "@/components/TodoForm.vue";
import TodoItem from "@/components/TodoItem.vue";
const todoList = ref([]);

watch(todoList, () => {
    setTodoListLocalStorage();
    },
    { deep: true }
);

const todoCompleted = computed(() => {
    return todoList.value.length > 0 &&
        todoList.value.every((todo) => todo.isCompleted);
});

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
};

const toggleTodoComplete = (todoPos) => {
    todoList.value[todoPos].isCompleted = !todoList.value[todoPos].isCompleted;
};

const toggleEditTodo = (todoPos) => {
    todoList.value[todoPos].isEditing = !todoList.value[todoPos].isEditing;
};

const updateTodo = (todoVal, todoPos) => {
    todoList.value[todoPos].todo = todoVal;
};

const deleteTodo = (todoId) => {
    todoList.value = todoList.value.filter((todo) => todo.id !== todoId);
};

/* drag & drop logic */

const dragSrcIndex = ref(null);

const handleDragStart = (index) => {
  dragSrcIndex.value = index;
};

const handleDrop = (targetIndex) => {
  if (dragSrcIndex.value === null) return;

  const from = dragSrcIndex.value;
  const to = targetIndex;

  if (from === to) {
    dragSrcIndex.value = null;
    return;
  }

  const movedItem = todoList.value[from];

  // remove from old position
  todoList.value.splice(from, 1);
  // insert at new position
  todoList.value.splice(to, 0, movedItem);

  dragSrcIndex.value = null;
};

</script>

<template>
    <main>
        <h1> Create Todo:</h1>
        <TodoForm @create-todo="createTodo"/>
        <ul class="todo-list" v-if="todoList.length > 0">
            <TodoItem
                v-for="(todo, index) in todoList" 
                :todo="todo"
                :key="todo.id"
                :index="index" 
                @toggle-complete="toggleTodoComplete"
                @edit-todo="toggleEditTodo"
                @update-todo="updateTodo"
                @delete-todo="deleteTodo"
                @drag-start="handleDragStart"
                @drop-item="handleDrop"
            />
        </ul>
        <p class="todos-msg" v-else>
            <span>Are you sure you have nothing to do?</span>
            <Icon icon="noto:thinking-face" width="22" />
        </p>
        <p v-if="todoCompleted && todoList.length > 0" class="todos-msg">
            <span>You have completed all your todos!</span>
            <Icon icon="noto-v1:party-popper" width="30"/>
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