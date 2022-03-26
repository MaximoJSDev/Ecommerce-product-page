<script setup>
import MainImages from './MainImages.vue';
import MainInfo from './MainInfo.vue';

</script>

<template>
  <main class="product">
    <MainImages />
    <MainInfo />
  </main>
</template>

<style>
.product {
  display: flex;
  flex-direction: column;
  margin: auto;
  max-width: 600px;
}
</style>
