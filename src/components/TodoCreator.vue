<script setup>
</script>

<template>
    <div class="input-wrap">
        <input type="text" placeholder="Enter your task here..." />
        <button>Add Task</button>
    </div>
</template>

<style scoped>
    .input-wrap {
        display: flex;
        transition: 250ms ease;
        border: 2px solid orange;
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

    button {
        background-color: orange;
        color: white;
        border: none;
        padding: 8px 16px;
        cursor: pointer;
        &:hover {
            background-color: darkorange;
        }
    }
</style>