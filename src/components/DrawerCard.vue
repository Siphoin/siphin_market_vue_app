<script setup>
import DrawerCardHead from './DrawerCardHead.vue';
import ProductMarketCardList from './ProductMarketCardList.vue';
import { inject } from 'vue';
const {cart} = inject('cart');
const {calculateTotalPrice} = inject('cartActions');
const {clearCart} = inject('cartActions');
</script>
<template>
    <div class="fixed top-0 left-0 h-full w-full opacity-70 bg-black z-10 bg"></div>
    <div class="bg-white w-96 h-full fixed right-0 top-0 z-20 p-8 product-list">
        <DrawerCardHead @closeCartWindow="closeCartWindow">
        </DrawerCardHead>
        <ProductMarketCardList/>
        <div class="flex flex-col gap-4 mb-6" v-if="cart.length > 0">
            <div class="flex gap-2">
                <span>Итого</span>
                <div class="flex-1 border-b border-dashed"></div>
                <B>{{calculateTotalPrice()}} ₽</B>
            </div>

            <div class="flex gap-2">
                <span>Налог</span>
                <div class="flex-1 border-b border-dashed"></div>
                <B>5%</B>
            </div>

            <div class="items-center">
            <button class="buttonCart py-3 mt-4" @click="clearCart">Оформить заказ</button>
        </div>
        </div>

        <div v-if="cart.length == 0">
            <p>В корзине ничего нет</p>
        </div>
    </div>
</template>

<style>
.bg {
    backdrop-filter: blur(20px);
}

.buttonCart {
	box-shadow: -1px 4px 17px 4px #736f27;
	background:linear-gradient(to bottom, #dae036 5%, #b3b352 100%);
	background-color:#dae036;
	border-radius:11px;
	border:1px solid #7b8f29;
	display:inline-block;
	cursor:pointer;
	color:#ffffff;
	font-family:Verdana;
	font-size:16px;
	font-weight:bold;
	padding:6px 30px;
	text-decoration:none;
}
.buttonCart:hover {
	background:linear-gradient(to bottom, #b3b352 5%, #dae036 100%);
	background-color:#b3b352;
}
.buttonCart:active {
	position:relative;
	top:1px;
}

/* Assuming the product list container has a class named 'product-list' */
.product-list {
  overflow-y: auto; /* Enable vertical scrolling if the content exceeds the container height */
}



</style>