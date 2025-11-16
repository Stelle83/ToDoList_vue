<script setup>
</script>

<template>
    <button>
        <slot>Add Task</slot>
    </button>    
</template>

<style scoped>
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
