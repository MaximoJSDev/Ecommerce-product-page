<script setup>
defineProps({
  id: String,
  isShowImg: {type: Boolean, default: false},
  isPreviewImg: {type: Boolean, default: false},
});
const getImgUrl = (name, isPreviewImg) => {
  const src = isPreviewImg 
    ? new URL(`../assets/image-product-${name}-thumbnail.jpg`, import.meta.url).href
    : new URL(`../assets/image-product-${name}.jpg`, import.meta.url).href
  return src;
};
const getImgClass = (isPreviewImg, isShowImg) => {
  const classImg = isPreviewImg
    ? ''
    : `product__slider__image ${isShowImg && 'imageSliderShow'}`
  return classImg;
};
</script>
<template>
  <img
    :class="getImgClass(isPreviewImg, isShowImg)"
    :src="getImgUrl(id, isPreviewImg)"
    :alt="`image-product-${id}`"
    :data-id="id"
  >
</template>