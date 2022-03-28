<script setup>
import ProductImage from './ProductImage.vue';

const handleClickSlider = (direction) => {
  const sliders = [...document.querySelectorAll(".product__slider__image")]
  const currentElement = Number(document.querySelector(".imageSliderShow").dataset.id);
  let valueDirection = currentElement + direction;
  if (valueDirection === 0 || valueDirection == sliders.length+1) {
    valueDirection = valueDirection === 0 ? sliders.length : 1;
  }
  sliders[currentElement-1].classList.toggle("imageSliderShow");
  sliders[valueDirection-1].classList.toggle("imageSliderShow");
};

const handleClickImagePreview = ({target}) => {
  [...target.parentElement.children].forEach((element) => {
    element.classList.remove("imgPreview--active")
  })
  target.classList.add("imgPreview--active")
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
      <ProductImage id="1" :isShowImg="true" :isPreview="false" />
      <ProductImage id="2" :isPreviewImg="false" />
      <ProductImage id="3" :isPreviewImg="false" />
      <ProductImage id="4" :isPreviewImg="false" />
    </div>
    <figure class="product__figure">
      <ProductImage id="1" :isPreviewImg="true" @click="handleClickImagePreview" />
      <ProductImage id="2" :isPreviewImg="true" @click="handleClickImagePreview" />
      <ProductImage id="3" :isPreviewImg="true" @click="handleClickImagePreview" />
      <ProductImage id="4" :isPreviewImg="true" @click="handleClickImagePreview" />
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