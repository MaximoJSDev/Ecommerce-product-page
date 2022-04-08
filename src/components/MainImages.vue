<script setup>
import { inject } from 'vue';
import ProductImage from './ProductImage.vue';
import ProductImageThumbnail from './ProductImageThumbnail.vue';

const containerFocus = inject("containerFocus");

const handleClickSlider = (direction, positionDef) => {
  // Slider de imagenes (Normal)
  selecSlider(direction, ".product__slider__image", false, positionDef);
  // Slider de imagenes (thumbnail)
  selecSlider(direction, ".product__figure div", true, positionDef);
};

const selecSlider = (direction, classImg, isThumbnail, positionDef) => {
  const sliders = [...document.querySelectorAll(classImg)];
  const slider1 = sliders.splice(0, sliders.length/2);
  const slider2 = sliders.splice(0, sliders.length);
  const selector = isThumbnail ? "imgThumbnail--active" : "imageSliderShow"
  const currentElement = Number(document.querySelector("."+selector).dataset.id);
  let valueDirection = positionDef ? positionDef : currentElement + direction;
  if (valueDirection === 0 || valueDirection == slider1.length+1) {
    // Si llega al limite del slider, se reinicia
    valueDirection = valueDirection === 0 ? slider1.length : 1;
  }
  changeImageToShow(slider1, slider2, currentElement, valueDirection, selector)
}

const changeImageToShow = (slider1, slider2, currentElement, valueDirection, selector) => {
  // Remueve la clase activa anterior (IMG)
  slider1[currentElement-1].classList.remove(selector);
  slider2[currentElement-1].classList.remove(selector);
  // Agrega la clase activa nueva (IMG)
  slider1[valueDirection-1].classList.add(selector);
  slider2[valueDirection-1].classList.add(selector);
}

const handleClickImageThumbnail = ({target}) => {
  containerFocus.value.classList.add("show")
  handleClickSlider(0, target.dataset.id)
};
</script>
<template>
  <div class="product__images">
    <div class="product__slider">
      <div class="product__slider__btnContainer">
        <div class="btn btn-left" @click="handleClickSlider(-1)">
          <img src="../assets/icon-previous.svg" alt="icon previous">
        </div>
        <div class="btn btn-right" @click="handleClickSlider(1)">
          <img src="../assets/icon-next.svg" alt="icon next">
        </div>
      </div>
      <ProductImage id="1" :isShowImg="true" />
      <ProductImage id="2" />
      <ProductImage id="3" />
      <ProductImage id="4" />
    </div>
    <figure class="product__figure">
      <ProductImageThumbnail id="1" @click="handleClickImageThumbnail" :isActiveImg="true" />
      <ProductImageThumbnail id="2" @click="handleClickImageThumbnail" />
      <ProductImageThumbnail id="3" @click="handleClickImageThumbnail" />
      <ProductImageThumbnail id="4" @click="handleClickImageThumbnail" />
    </figure>
  </div>
</template>
<style>
.product__images {
  display: flex;
  width: 100%;
}
.product__slider {
  position: relative;
  width: 100%;
  height: 27.8125rem;
  display: flex;
  overflow-x: hidden;
  user-select: none;
}
.product__slider__btnContainer {
  width: 100%;
  position: absolute;
  top: 0;
  bottom: 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: auto;
  padding-inline: 5%;
  z-index: 22;
}
.btn {
  width: 3.125rem;
  height: 3.125rem;
  background-color: #fff;
  border-radius: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}
.btn img {
  height: 1.125rem;
}
.product__slider__image {
  width: 100%;
  height: 100%;
  position: absolute;
  object-fit: cover;
  opacity: 0;
  transition: .6s;
  z-index: -1;
}
.imageSliderShow {
  opacity: 1;
  z-index: 11;
}
.product__figure {
  display: none;
}
</style>