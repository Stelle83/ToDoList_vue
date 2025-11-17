<script setup>
  import Summary from '@/components/Summary.vue';
  import ListOfTasks from '@/components/ListOfTasks.vue';
  import Header from '@/components/Header.vue';

</script>

<template>

  <Header/>

  <ListOfTasks/>

  <Summary />

</template>

<style>
* {
  font-family: "Rubik", sans-serif;
}

.container {
  max-width: 480px;
  margin: 1rem;
}


</style>