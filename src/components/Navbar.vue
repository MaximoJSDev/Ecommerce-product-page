<script setup>

</script>

<template>
  <header class="header">
    <div class="header__menu">
      <img class="header__iconMenu" src="../assets/icon-menu.svg" alt="icon menu">
      <img class="header__logo" src="../assets/logo.svg" alt="logo">
    <div class="header__menu__linksContainer">
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
      <img class="header__profile__cart" src="../assets/icon-cart.svg" alt="icon cart">
      <img class="header__profile__avatar" src="../assets/image-avatar.png" alt="image avatar">
    </div>
  </header>
</template>

<style scoped>
.header {
  max-width: 80rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1.625rem 1.875rem;
  margin: auto;
}
.header div:not(.header__menu__linksContainer) {
  display: flex;
  align-items: center;
  justify-content: space-between;
  column-gap: 1.5625rem;
}
.header__iconMenu {
  height: 1.25rem;
  align-self: center;
  margin-top: .25rem;
}
.header__logo {
  height: 1.75rem;
}
.header__profile__cart {
  height: 1.5rem;
}
.header__profile__avatar {
  height: 2.375rem;
}
.header__menu__linksContainer {
  display: none;
}
.header__menu__linksContainer ul {
  display: flex;
  justify-content: center;
  align-items: center;
  list-style: none;
  column-gap: 1.875rem;
  font-size: 1.125rem;
  margin-left: 2.1875rem;
}
.header__menu__linksContainer li {
  cursor: pointer;
}
</style>
