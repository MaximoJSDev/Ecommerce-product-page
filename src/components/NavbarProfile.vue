<script setup>
import { inject } from 'vue';

const display = inject("display");
const products = inject("cart");

const showCart = () => {
  display.value = display.value == "none" 
    ? "block" 
    : "none"
}
</script>
<template>
  <div class="header__profile">
    <div class="header__profile__cart" @click="showCart">
      <span class="header__profile__cart__notification" v-if="products !== undefined">
        {{products.toCarry}}
      </span>
      <img src="../assets/icon-cart.svg" alt="icon cart">
    </div>
    <img class="header__profile__avatar" src="../assets/image-avatar.png" alt="image avatar">
  </div>
</template>