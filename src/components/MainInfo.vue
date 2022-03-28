<script setup>
import { ref,computed } from 'vue';

const counter = ref(1)
let price = ref(250);
let discountPercentage = ref(50);

const calcDiscountedPrice = computed(() => {
  return (discountPercentage.value / 100 * price.value) * counter.value
})
const handleCounter = (num) => {
  if (counter.value >= 1) {
    if (counter.value == 1 && num == -1) return
    counter.value += num
  }
}
</script>
<template>
  <div class="product__info">
    <h3 class="product__info__company">Sneaker Company</h3>
    <h1 class="product__info__title">Fall Limited Edition Sneakers</h1>
    <p class="product__info__text">These low-profile sneakers are you perfect casual wear companion. Featuring a durable rubber outer sole, they'll withstand everything the weather can offer.</p>
    <div class="product__info__priceContainer">
      <div>
        <span class="price">
          ${{
            calcDiscountedPrice % 1 === 0
              ? calcDiscountedPrice + ".00"
              : calcDiscountedPrice
          }}
        </span>
        <span class="percentageDiscount">
          50%
        </span>
      </div>
      <div class="discount">
        ${{price}}.00
      </div>
    </div>
    <div class="btnContainer">
      <button class="bigBtn btn-count">
        <span class="btn-count__symbol" @click="handleCounter(-1)">-</span>
          <span>{{counter}}</span>
        <span class="btn-count__symbol" @click="handleCounter(1)">+</span>
      </button>
      <button class="bigBtn btn-orange">
        <img src="../assets/icon-cart-white.svg" alt="icon cart">
        Add to cart
      </button>
    </div>
  </div>
</template>
<style>
.product__info {
  display: flex;
  flex-direction: column;
  padding: 30px 28px;
  margin-bottom: 5rem;
}
.product__info__company {
  color: var(--Orange);
  text-transform: uppercase;
  font-size: 16px;
  letter-spacing: 2px;
  margin-bottom: 15px;
}
.product__info__title {
  font-weight: 700;
  font-size: 37px;
  margin-bottom: 15px;
}
.product__info__text {
  font-size: 20px;
  line-height: 32px;
  color: var(--Dark-grayish-blue);
}
.product__info__priceContainer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: 40px;
  margin-bottom: 7px;
  font-weight: 700;
}
.product__info__priceContainer > div {
  display: flex;
  align-items: center;
  column-gap: 20px;
}
.price {
  font-size: 37px;
}
.percentageDiscount {
  font-size: 22px;
  color: var(--Orange);
  background-color: var(--Pale-orange);
  padding: 5px 9px;
  border-radius: 10px;
}
.discount {
  font-size: 21px;
  color: var(--Grayish-blue);
  text-decoration: line-through;
}
.btnContainer {
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.bigBtn {
  font-family: 'Kumbh Sans', sans-serif;
  font-size: 22px;
  font-weight: 700;
  display: flex;
  align-items: center;
  padding: 22px 30px;
  border-radius: 13px;
  border: none;
  margin-top: 22px;
}
.btn-count {
  justify-content: space-between;
  background-color: var(--Light-grayish-blue);
}
.btn-count__symbol {
  font-size: 36px;
  font-weight: 700;
  line-height: 24px;
  color: var(--Orange);
  cursor: pointer;
}
.btn-orange {
  justify-content: center;
  column-gap: 20px;
  background-color: var(--Orange);
  color: #fff;
  box-shadow: 0 33px 50px -17px #ff7d1a87;
  cursor: pointer;
}
</style>