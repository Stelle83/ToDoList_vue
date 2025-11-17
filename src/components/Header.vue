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
    <header>
        <nav class="container">
            <div class=top-nav>
                <img class="logo" src="@/assets/images/logo.png" alt="Logo" />
                <h2>To-Do List</h2>
            </div>
            <div>{{ currentDate }}</div>
        </nav>
    </header>
</template>

<style scoped>
    * {
        color: green;
    }
   
    .top-nav {
        display: flex;
        align-items: center;
        gap: 10px;
    }
</style>
