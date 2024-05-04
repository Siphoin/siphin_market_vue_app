<script setup>
import { defineProps } from 'vue';
  defineProps({
    title: String,
    img: String,
    price: Number,
    priceDiscount: Number,
    isDiscount: Boolean,
    InCard: Boolean,
    Add: Function
  });

</script>
<template>
          <div class="relative m-10 rounded-3xl p-8  element">
        <img :src='img' alt="" class="icon_card">
        <p class="label_card mt-2">
            {{ title }}
        </p>
        <div>
        <p class="price_card_enable" v-if="!isDiscount">
            {{ price }} ₽
            
        </p>

        <p class="price_card_disable" v-if="isDiscount">
            {{ price }} ₽
            
        </p>
        
        <p class="price_card_discount" v-if="isDiscount">
            {{ priceDiscount }} ₽
        </p>
        </div>
        <div class="grid gap-3">
          <button class="buttonBuy" v-if="!InCard" @click="Add">Добавить в корзину</button>
          <button href="#" class="buttonRemove" v-if="InCard"  @click="Add">Удалить из корзины</button>
        </div>
      </div>

</template>

<style>
.icon_card {
  width: 200px;
  height: 200px;
}

.label_card {
  color: white;
}

.price_card {
  margin-right: 20px;
  margin-top: 3px;
  font-weight: bold;
}

.price_card_disable {
  color: rgba(165, 165, 165, 0.829);
  text-decoration: line-through;
  text-decoration-color: red;
}

.price_card_enable {
  color: rgba(255, 251, 0, 0.829);
}

.price_card_discount {
  color: rgba(9, 255, 0, 0.829);
  font-weight: bold;
  
}

.element {
  background-color: rgb(34, 34, 34);
  box-shadow: 0px 7px 14px 15px #73276f;
}

.buttonBuy {
  margin-top: 12px;
	box-shadow: 0px 10px 14px -7px #736d27;
	background:linear-gradient(to bottom, #b3a759 5%, #b3a652 100%);
	background-color:#b3a759;
	border-radius:4px;
	border:1px solid #8f8729;
	display:inline-block;
	cursor:pointer;
	color:#ffffff;
	font-family:Arial;
	font-size:13px;
	font-weight:bold;
	padding:6px 12px;
	text-decoration:none;
	text-shadow:0px 1px 0px #8a8a3d;
}
.buttonBuy:hover {
	background:linear-gradient(to bottom, #b3a652 5%, #b3a759 100%);
	background-color:#b3a652;
}
.buttonBuy:active {
	position:relative;
	top:1px;
}

.buttonRemove {
  margin-top: 12px;
	box-shadow: 0px 10px 14px -7px #732727;
	background:linear-gradient(to bottom, #b35959 5%, #b35252 100%);
	background-color:#b3a759;
	border-radius:4px;
	border:1px solid #8f2929;
	display:inline-block;
	cursor:pointer;
	color:#ffffff;
	font-family:Arial;
	font-size:13px;
	font-weight:bold;
	padding:6px 12px;
	text-decoration:none;
	text-shadow:0px 1px 0px #8a3d3d;
}
.buttonRemve:hover {
	background:linear-gradient(to bottom, #b35252 5%, #b35959 100%);
	background-color:#b35252;
}
.buttonRemve:active {
	position:relative;
	top:1px;
};
</style>
