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
  font-size: 15px;
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
    padding: 2.1875rem 0 2.5rem !important;
    border-bottom: .0625rem solid var(--Grayish-blue);
  }
  .header__iconMenu {
    display: none;
  }
  .header__menu__linksContainer {
    display: block !important;
  }
  .header__profile__avatar {
    height: 3.5625rem !important;
  }
  .cart {
    top: 102px;
    margin-right: -1.75rem;
  }
  .product {
    max-width: 75rem;
    flex-direction: row;
    margin-top: 5rem;
  }
  .product__images {
    flex-direction: column;
    row-gap: 1.5625rem;
  }
  .product__slider {
    height: 32.5rem;
    border-radius: 1.25rem;
  }
  .product__images:not(.containerFocus .product__images) .product__slider__btnContainer {
    display: none;
  }
  .product__figure {
    display: flex;
    gap: 1.45rem;
    justify-content: space-between;
  }
  .product__figure img {
    height: 6.875rem;
    border-radius: .625rem;
  }
  .product__figure div {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 11;
    cursor: pointer;
  }
  .imgThumbnail--active {
    outline: 0.2rem solid var(--Orange);
    border-radius: 0.625rem;
    overflow: hidden;
  }
  .product__figure div::after {
    content: "";
    display: block;
    width: 100%;
    height: 100%;
    position: absolute;
    inset: 0;
    background-color: transparent;
    border-radius: 0.625rem;
  }
  .product__figure div.imgThumbnail--active::after {
    background-color: rgba(255, 255, 255, 0.68);
  }
  .product__figure div:hover:not(.imgThumbnail--active):after {
    background-color: rgba(255, 255, 255, 0.4);
  }
  .product__info {
    justify-content: center;
    padding-left: 9rem;
    margin-bottom: 0;
  }
  .product__info__company {
    font-size: 1.0625rem;
  }
  .product__info__title {
    font-size: 2.875rem;
    margin-bottom: 2.5rem;
  }
  .product__info__priceContainer {
    flex-direction: column;
    align-items: flex-start;
    row-gap: .625rem;
  }
  .btnContainer {
    flex-direction: row;
    justify-content: unset;
    align-items: center;
    column-gap: 1.5625rem;
  }
  .btn-count {
    width: 35%;
  }
  .btn-orange {
    width: 77%;
  }
}

</style>
