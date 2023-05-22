<script setup>
import Balance from './components/Balance.vue';
import Spending from './components/Spending.vue';


</script>

<template>
  <main>
    <Balance />

    <Spending />
  </main>
</template>

<style scoped>
  main {
    width: 350px;

    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }

  main > * {
    margin: 5% 0;
  }
</style>
