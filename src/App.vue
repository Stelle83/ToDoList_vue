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
  margin: 20;
  padding: 0;
  box-sizing: border-box;
}

.container {
  max-width: 1100px;
  margin: 0 auto;
}


</style>