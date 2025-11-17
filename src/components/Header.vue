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
                <h1>To-Do List</h1>
            </div>
            <div>{{ currentDate }}</div>
        </nav>
    </header>
</template>

<style scoped>
    h1 {
        color: green;
    }

    * {
    color: orange;
}

    .top-nav {
        display: flex;
        align-items: center;
        gap: 10px;
    }
</style>
