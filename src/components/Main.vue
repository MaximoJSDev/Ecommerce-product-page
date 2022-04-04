<script setup>
import { ref } from 'vue';
import MainImages from './MainImages.vue';
import MainInfo from './MainInfo.vue';
import IconClose from './Icons/IconClose.vue';

const containerFocus = ref(null);

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

const exitImageFocus = ({target}) => {
  if (
    target.classList.contains("containerFocus") || 
    target.classList.contains("containerFocus__iconClose") ||
    target.classList.contains("containerFocus__iconClose__img")
  ) {
    containerFocus.value.classList.remove("show");
  }
}
</script>
<template>
  <main class="product">
    <MainImages 
      :handleClickSlider="handleClickSlider" 
      :handleClickImageThumbnail="handleClickImageThumbnail" 
    />
    <MainInfo />
    <section class="containerFocus" ref="containerFocus" @click="exitImageFocus">
      <div class="containerFocus__iconClose">
        <IconClose />
      </div>
      <MainImages 
        :handleClickSlider="handleClickSlider" 
        :handleClickImageThumbnail="handleClickImageThumbnail"
      />
    </section>
  </main>
</template>
<style>
.product {
  display: flex;
  flex-direction: column;
  margin: auto;
  max-width: 600px;
}
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
