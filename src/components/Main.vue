<script setup>

</script>

<template>
  <main class="product">
    <div class="product__images">
      <div class="product__images__btnContainer">
        <div class="btn btn-left">
          <img src="../assets/icon-previous.svg" alt="icon previous">
        </div>
        <div class="btn btn-right">
          <img src="../assets/icon-next.svg" alt="icon next">
        </div>
      </div>
      <img class="product__images__image" src="../assets/image-product-1.jpg" alt="">
    </div>
    <div class="product__info"></div>
  </main>
</template>

<style scoped>
.product {
  display: flex;
  flex-direction: column;
  margin: auto;
  max-width: 600px;
}
.product__images {
  position: relative;
}
.product__images__btnContainer {
  width: 100%;
  position: absolute;
  top: 0;
  bottom: 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: auto;
  padding-inline: 5%;
}
.btn {
  width: 50px;
  height: 50px;
  background-color: #fff;
  border-radius: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  
}
.btn img {
  height: 18px;
}
.product__images__image {
  width: 100%;
  height: 445px;
  object-fit: cover;
}
</style>
