<script setup>
import CardItem from './CardItem.vue';
import { inject } from 'vue';
const {cart} = inject('cart');
const {removeFromCart} = inject('cartActions')
</script>
<template>
    <div class="flex flex-col gap-4">
    <CardItem v-for="item in cart" :key="item.id" 
    :price="item.isDiscount ? item.priceDiscount : item.price"
    :img="item.img"
    :Remove="() => removeFromCart(item)"
    :title="item.title">
    
    </CardItem>
    </div>
</template>
