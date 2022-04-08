<script setup>
import { inject } from 'vue';

const display = inject("display");
const products = inject("cart");
</script>
<template>
<div class="cart" :style="{ display: display }">
  <h6 class="cart__title">Cart</h6>
  <div class="cart__body" v-if="products !== undefined">
    <div class="cart__product">
      <img 
        class="cart__product__img"
        src="../assets/image-product-1-thumbnail.jpg" 
        alt="image-product-1-thumbnail"
      >
      <div>
        <h6 class="cart__product__name">{{products.name}}</h6>
        <div class="cart__product__details">
          <span class="product-price">${{products.price}}</span>
          <span class="product-number">x {{products.toCarry}}</span>
          <span class="product-total">${{products.total}}</span>
        </div>
      </div>
      <img 
        class="cart__product__delete" 
        src="../assets/icon-delete.svg" 
        alt="icon delete" 
        @click="clearCart"
      >
    </div>
    <button class="cart__body__btn bigBtn btn-orange">Checkout</button>
  </div>
  <div class="cart__isEmpty" v-else>Your cart is Empty.</div>
</div>
</template>
<style>
.cart {
  width: 95%;
  max-width: 440px;
  position: absolute;
  top: 97px;
  left: 0;
  right: 0;
  margin: auto;
  background-color: #fff;
  padding: 30px;
  border-radius: 10px;
  box-shadow: 0 30px 40px -12px #949699a3;
  z-index: 26;
}
@media (min-width: 575px) {
  .cart {
    margin-right: 1.75rem;
  }
}
.cart__title {
  font-size: 19px;
  padding-bottom: 30px;
  margin-bottom: 30px;
  border-bottom: 1px solid var(--Grayish-blue);
}
.cart__body__btn.btn-orange {
  font-size: 18px;
  width: 100%;
  padding-block: 20px;
  box-shadow: 0 13px 30px -7px #ff7d1a2d !important;
}
.cart__product {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 30px;
}
.cart__product__img {
  height: 65px;
  border-radius: 8px;
}
.cart__product__name {
  font-size: 20px;
  font-weight: 400;
  margin-bottom: 5px;
}
.cart__product__details {
  font-size: 18.5px;
}
.cart__product__details span {
  margin-right: 7px;
}
.product-total {
  font-weight: 700;
}
.cart__product__delete {
  height: 20px;
  cursor: pointer;
}

.cart__isEmpty {
  width: 100%;
  height: 158px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 15.5px;
  font-weight: 600;
  color: var(--Very-vark-blue);
}
</style>