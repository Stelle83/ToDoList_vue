<script setup>
import { reactive, defineEmits } from "vue";
import ToDoButton from "@/ToDoButton.vue";

const emit = defineEmits(["create-todo"]);

const todoState = reactive({
    todo: "",
    invalid: null,
    errMsg: "",
});

const createTodo = () => {
    todoState.invalid = null;
    if (todoState.todo !== "") {
        emit("create-todo", todoState.todo);
        todoState.todo = "";
        return;
    }
    todoState.invalid = true;
    todoState.errMsg = "Task cannot be empty!";
};
</script>

<template>
    <div class="input-wrap" :class="{ 'input-err': todoState.invalid }">
        <input type="text" placeholder="Enter your task here..." v-model="todoState.todo" />
        <ToDoButton @click="createTodo()" />
    
    </div>
<p v-show="todoState.invalid" class="err-msg"> {{ todoState.errMsg }}</p>

</template>

<style scoped>
    .input-wrap {
        display: flex;
        transition: 250ms ease;
        border: 2px solid orange;

        &.input-err {
            border-color: red;
        }

        &:focus-within {
          /*  box-shadow: 0 -4px 6px -1px rgb(0 0 0 / 0.1),
            0 -2px 4px -2px rgb(0 0 0 / 0.1); */
           box-shadow: 0 0 6px orange;
        }
    }

    input {
        width: 100%;
        padding: 8px 6px;
        border: none;
        &:focus {
            outline: 2px solid orange;
        }
    }

    .err-msg {
        color: red;
        margin-top: 6px;
        font-size: 12px;
        text-align: center;
    }   
</style>