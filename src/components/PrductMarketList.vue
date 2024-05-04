<script setup>
import { defineProps } from 'vue';
import {inject} from 'vue';
  defineProps({
    items: Array
  });
import ProductMarket from './ProductMarket.vue';
const {addToCart} = inject('cartActions')
</script>
<template>
        <div class="grid grid-cols-4 gap-6">
            <ProductMarket v-for="item in items" :key="item.id"
            :img="item.img" 
            :price="item.price" 
            :priceDiscount="item.priceDiscount"
            :InCard="item.isAdded"
            :isDiscount="item.isDiscount"
            :Add="() => addToCart(item)"
            :title="item.title">
            

            </ProductMarket>
    </div>
</template>