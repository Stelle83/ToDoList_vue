<script setup>
  import ListOfTasks from '@/components/ListOfTasks.vue';
  import Header from '@/components/Header.vue';
</script>

<template>

  <Header/>

  <ListOfTasks/>

</template>

<style>
* {
  font-family: "Rubik", sans-serif;
}

.container {
  max-width: 480px;
  margin: 1rem;
}

@media (min-width: 800px) {
.container {
  width: 1000px;
  margin: 2rem;
}}
</style>