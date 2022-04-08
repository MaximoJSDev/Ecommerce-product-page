<script setup>
import { inject } from "vue";
import MainImages from "./MainImages.vue";
import IconClose from "./Icons/IconClose.vue";

const containerFocus = inject("containerFocus")
const exitImageFocus = ({target}) => {
  if (
    target.classList.contains("containerFocus") || 
    target.classList.contains("containerFocus__iconClose") ||
    target.classList.contains("containerFocus__iconClose__svg") ||
    target.classList.contains("containerFocus__iconClose__path")
  ) {
    containerFocus.value.classList.remove("show");
  }
}
</script>
<template>
  <div class="containerFocus" ref="containerFocus" @click="exitImageFocus">
    <div class="containerFocus__iconClose">
      <IconClose />
    </div>
    <MainImages />
  </div>
</template>
<style>
.containerFocus {
  width: 100%;
  position: absolute;
  inset: 0;
  display: none;
  justify-content: center;
  align-items: center;
  background-color: rgba(0, 0, 0, 0.73);
  z-index: 33;
}
.containerFocus.show {
  display: flex;
}
.containerFocus__iconClose {
  width: 637px;
  height: 840px;
  position: absolute;
  display: flex;
  align-items: flex-start;
  justify-content: flex-end;
}
.containerFocus__iconClose__img {
  width: 25px;
  cursor: pointer;
}
.containerFocus .product__images {  
  width: 520px;
  transform: scale(1.225);
}
.containerFocus .product__slider {
  overflow-x: unset;
}
.containerFocus .product__slider__image {
  border-radius: 20px;
}
.containerFocus .product__slider__btnContainer {
  padding-inline: 0;
}
.containerFocus .btn:first-of-type {
  transform: translateX(-50%);
}
.containerFocus .btn:last-of-type {
  transform: translateX(50%);
}
.containerFocus .product__figure {
  justify-content: center;
}
.containerFocus .product__figure img {
  height: 90px;
}
</style>