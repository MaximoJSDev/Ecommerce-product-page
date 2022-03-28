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
  padding: 1.875rem 1.75rem;
  margin-bottom: 5rem;
}
.product__info__company {
  color: var(--Orange);
  text-transform: uppercase;
  font-size: 1rem;
  letter-spacing: .125rem;
  margin-bottom: .9375rem;
}
.product__info__title {
  font-weight: 700;
  font-size: 2.3125rem;
  margin-bottom: .9375rem;
}
.product__info__text {
  font-size: 1.25rem;
  line-height: 2rem;
  color: var(--Dark-grayish-blue);
}
.product__info__priceContainer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: 2.5rem;
  margin-bottom: .4375rem;
  font-weight: 700;
}
.product__info__priceContainer > div {
  display: flex;
  align-items: center;
  column-gap: 1.25rem;
}
.price {
  font-size: 2.3125rem;
}
.percentageDiscount {
  font-size: 1.375rem;
  color: var(--Orange);
  background-color: var(--Pale-orange);
  padding: .3125rem .5625rem;
  border-radius: .625rem;
}
.discount {
  font-size: 1.3125rem;
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
  font-size: 1.375rem;
  font-weight: 700;
  display: flex;
  align-items: center;
  padding: 1.375rem 1.875rem;
  border-radius: .8125rem;
  border: none;
  margin-top: 1.375rem;
}
.btn-count {
  justify-content: space-between;
  background-color: var(--Light-grayish-blue);
  align-items: baseline;
}
.btn-count__symbol {
  font-size: 2.25rem;
  font-weight: 700;
  line-height: 1.5rem;
  color: var(--Orange);
  cursor: pointer;
}
.btn-orange {
  justify-content: center;
  column-gap: 1.25rem;
  background-color: var(--Orange);
  color: #fff;
  box-shadow: 0 2.0625rem 3.125rem -1.0625rem #ff7d1a87;
  cursor: pointer;
}
</style>