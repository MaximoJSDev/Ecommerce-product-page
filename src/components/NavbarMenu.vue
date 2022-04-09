<script setup>
import { ref } from 'vue';

const menuContent = ref(null);
const marker = ref(null);
const links = ref([]);
const list = ["Collections", "Men", "Women", "About", "Contact"];

const toggleMenu = () => {
  menuContent.value.classList.toggle("showMenu");
}

const moveIndicator = (e) => {
  marker.value.style.left = e.target.offsetLeft+'px';
  marker.value.style.width = e.target.offsetWidth+'px';
}
</script>
<template>
<div class="header__menu">
  <img 
    class="header__iconMenu" 
    src="../assets/icon-menu.svg" 
    alt="icon menu" 
    @click="toggleMenu"
  >
  <img class="header__logo" src="../assets/logo.svg" alt="logo">
  <nav class="header__menu__linksContainer" ref="menuContent">
    <img 
      class="icon-close" 
      src="../assets/icon-close.svg" 
      alt="icon close" 
      @click="toggleMenu"
    >
    <ul class="header__menu__links">
      <li 
        v-for="(item,index) in list" 
        :ref="el => links.push(el)" 
        :key="index"
        @click="moveIndicator"
      >
        {{item}}
      </li>
      <div class="header__menu__marker" ref="marker"></div>
    </ul>
  </nav>
</div>
</template>