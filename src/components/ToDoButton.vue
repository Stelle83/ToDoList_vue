<script setup>
</script>

<template>
    <button>
        <slot>Add</slot>
    </button>    
</template>

<style scoped>
    button {
        background-color: orange;
        color: white;
        font-size: 14px;
        border: none;
        padding: 8px 16px;
        cursor: pointer;
        &:hover {
            background-color: darkorange;
        }
    }
</style>
