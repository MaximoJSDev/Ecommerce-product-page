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
@media (min-width: 1340px) {
  .header {
    padding: 35px 0 40px !important;
    border-bottom: 1px solid var(--Grayish-blue);
  }
  .header__iconMenu {
    display: none;
  }
  .header__menu__linksContainer {
    display: block !important;
  }
  .header__profile__avatar {
    height: 57px !important;
  }
  .product {
    max-width: 1200px;
    flex-direction: row;
    margin-top: 5rem;
  }
  .product__images {
    flex-direction: column;
    row-gap: 25px;
  }
  .product__slider {
    height: 520px;
    border-radius: 20px;
  }
  .product__figure {
    display: flex;
    gap: 20px;
    justify-content: space-between;
  }
  .product__figure img {
    height: 110px;
    border-radius: 10px;
  }
  .product__figure img:hover {
    opacity: .65;
  }
  .imgPreview--active {
    outline: 3px solid var(--Orange);
    opacity: .36;
  }
  .product__info {
    justify-content: center;
    padding-left: 9rem;
    margin-bottom: 0;
  }
  .product__info__company {
    font-size: 17px;
  }
  .product__info__title {
    font-size: 46px;
    margin-bottom: 40px;
  }
  .product__info__priceContainer {
    flex-direction: column;
    align-items: flex-start;
    row-gap: 10px;
  }
  .btnContainer {
    flex-direction: row;
    justify-content: unset;
    align-items: center;
    column-gap: 25px;
  }
  .btn-count {
    width: 35%;
  }
  .btn-orange {
    width: 77%;
  }
}

</style>
