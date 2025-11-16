<script setup>
    import {ref} from "vue"
    const isVisible = ref("SEE ON TEST TEKST") 
</script>

<template>
    <nav class="container">
        <h2>Summary Component</h2>
        <p>This is the summary of the application. {{ isVisible }}</p>
    </nav>
</template>

<style scoped>

* {
    color: rgb(204, 30, 67);
}
</style>