<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import Navbar from './components/Navbar.vue';
import Main from './components/Main.vue';
</script>

<template>
  <Navbar />
  <Main />
</template>

<style>
html {
  box-sizing: border-box;
}
*, *::after, *::before {
  margin: 0;
  padding: 0;
  box-sizing: inherit;
}
:root {
/* ### Primary */
--Orange: hsl(26, 100%, 55%);
--Pale-orange: hsl(25, 100%, 94%);

/* ### Neutral */
--Very-vark-blue: hsl(220, 13%, 13%);
--Dark-grayish-blue: hsl(219, 9%, 45%);
--Grayish-blue: hsl(220, 14%, 75%);
--Light-grayish-blue: hsl(223, 64%, 98%);
--White: hsl(0, 0%, 100%);
--Black: hsl(0, 0%, 0%); /*(with 75% opacity for lightbox background)*/
}
body {
  font-family: 'Kumbh Sans', sans-serif;
}
</style>
