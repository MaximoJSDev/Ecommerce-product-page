<script setup>
defineProps({
  id: String,
  isShowImg: {type: Boolean, default: false},
});
const getImgUrl = (name) => {
  return new URL(`../assets/image-product-${name}.jpg`, import.meta.url).href
};
const getImgClass = (isShowImg) => {
  return `product__slider__image ${isShowImg ? 'imageSliderShow' : ""}`
};
</script>
<template>
  <img
    :class="getImgClass(isShowImg)"
    :src="getImgUrl(id)"
    :alt="`image-product-${id}`"
    :data-id="id"
  >
</template>