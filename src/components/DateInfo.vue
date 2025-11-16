<script setup>
    import {ref} from 'vue';

    const currentDate = ref(new Date().toLocaleDateString('sv-SE', {
        weekday: 'long',
        year: 'numeric',
        month: 'long',
        day: 'numeric'
    }));

</script>

<template>
    <nav class="container">
        <h2>Date Component</h2>

        <div>{{ currentDate }}</div>
    </nav>



</template>

<style scoped>

* {
    color: orange;
}

</style>