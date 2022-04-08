<script setup>
import { provide, ref } from 'vue';
import MainImages from './MainImages.vue';
import MainInfo from './MainInfo.vue';
import MainFocus from './MainFocus.vue';

const containerFocus = ref(null);
provide("containerFocus",containerFocus);

</script>
<template>
  <main class="product">
    <MainImages />
    <MainInfo />
    <MainFocus />
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
