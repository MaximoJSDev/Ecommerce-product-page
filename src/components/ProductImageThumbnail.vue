<script setup>
defineProps({
  id: String,
  isActiveImg: {
    type: Boolean,
    default: false
  },
});
const getImgUrl = (name) => {
  return new URL(`../assets/image-product-${name}-thumbnail.jpg`, import.meta.url).href
};
</script>
<template>
  <div 
    :class="isActiveImg ? 'imgThumbnail--active' : ''" 
    :data-id="id"
  >
    <img
      :src="getImgUrl(id)"
      :alt="`image-product-${id}-thumbnail`"
    >
  </div>
</template>