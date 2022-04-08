<script setup>
import { inject, ref } from 'vue';
import NavbarCart from './NavbarCart.vue';

const menuContent = ref(null);
const display = inject("display");
const products = inject("cart");

const toggleMenu = () => {
  menuContent.value.classList.toggle("showMenu");
}
const showCart = () => {
  display.value = display.value == "none" 
    ? "block" 
    : "none"
}
</script>
<template>
  <header class="header">
    <div class="header__menu">
      <img class="header__iconMenu" src="../assets/icon-menu.svg" alt="icon menu" @click="toggleMenu">
      <img class="header__logo" src="../assets/logo.svg" alt="logo">
      <div class="header__menu__linksContainer" ref="menuContent">
        <img class="icon-close" src="../assets/icon-close.svg" alt="icon close" @click="toggleMenu">
        <ul class="links">
          <li>Collections</li>
          <li>Men</li>
          <li>Women</li>
          <li>About</li>
          <li>Contact</li>
        </ul>
      </div>
    </div>
    <div class="header__profile">
      <div class="header__profile__cart" @click="showCart">
        <span class="header__profile__cart__notification" v-if="products !== undefined">
          {{products.toCarry}}
        </span>
        <img src="../assets/icon-cart.svg" alt="icon cart">
      </div>
      <img class="header__profile__avatar" src="../assets/image-avatar.png" alt="image avatar">
    </div>
    <NavbarCart />
  </header>
</template>
<style scoped>
.header {
  position: relative;
  max-width: 80rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1.625rem 1.875rem;
  margin: auto;
}
.header > div:not(.cart) {
  display: flex;
  align-items: center;
  justify-content: space-between;
  column-gap: 1.5625rem;
}
.header__iconMenu {
  height: 1.25rem;
  align-self: center;
  margin-top: .25rem;
  cursor: pointer;
}
.header__logo {
  height: 1.75rem;
}
.header__profile__cart {
  position: relative;
  height: 1.5rem;
  width: 1.4rem;
  cursor: pointer;
}
.header__profile__cart img {
  width: 100%;
  height: 100%;
}
.header__profile__cart__notification {
  font-size: 11px;
  font-weight: 700;
  text-align: center;
  width: 26px;
  position: absolute;
  top: -10px;
  right: -10px;
  padding: 2px 7px;
  background-color: var(--Orange);
  color: #fff;
  border-radius: 9px;
}
.header__profile__avatar {
  height: 2.375rem;
}
.header__menu__linksContainer, .icon-close {
  display: none;
}
.header__menu__linksContainer ul {
  display: flex;
  justify-content: center;
  align-items: center;
  list-style: none;
  column-gap: 1.875rem;
  font-size: 1.185rem;
  margin-left: 2.1875rem;
}
.header__menu__linksContainer li {
  cursor: pointer;
}
@media (max-width: 1340px) {
  .header__menu__linksContainer {
    width: 22.625rem;
    min-height: 100vh;
    position: fixed;
    top: 0;
    left: 0;
    bottom: 0;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    background-color: #fff;
    padding-left: 2.0625rem;
    padding-top: 2.0625rem;
    box-shadow: 2rem 0 40px #00000069;
    z-index: 222;
  }
  .showMenu {
    display: flex;
  }
  .icon-close {
    display: block;
    height: 1.35rem;
    cursor: pointer;
    margin-bottom: 5rem;
  }
  .header__menu__linksContainer ul {
    flex-direction: column;
    margin-left: 0;
    align-items: flex-start;
    font-weight: 700;
    font-size: 1.35rem;
    row-gap: 2rem;
  }
}
</style>
