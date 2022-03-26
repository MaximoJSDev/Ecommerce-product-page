<script setup>

</script>

<template>
  <header class="header">
    <div class="header__menu">
      <img class="header__iconMenu" src="../assets/icon-menu.svg" alt="icon menu">
      <img class="header__logo" src="../assets/logo.svg" alt="logo">
    </div>
    <div class="header__profile">
      <img class="header__profile__cart" src="../assets/icon-cart.svg" alt="icon cart">
      <img class="header__profile__avatar" src="../assets/image-avatar.png" alt="image avatar">
    </div>
  </header>
</template>

<style scoped>
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 26px 30px;
}
.header div {
  display: flex;
  align-items: center;
  justify-content: space-between;
  column-gap: 25px;
}
.header__iconMenu {
  height: 20px;
  align-self: center;
  margin-top: 4px;
}
.header__logo {
  height: 28px;
}
.header__profile__cart {
  height: 27px;
}
.header__profile__avatar {
  height: 38px;
}
</style>
