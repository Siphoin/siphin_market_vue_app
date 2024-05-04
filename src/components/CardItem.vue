<script setup>
import { defineProps } from 'vue';
  defineProps({
    title: String,
    img: String,
    price: Number,
    priceDiscount: Number,
    isDiscount: Boolean,
    Remove: Function
  });

</script>
<template>
    <div class="border border-slate-100 p-4 rounded-xl gap-4">
        <img :src="img" alt="carditem" class="icon">
        <div class="flex flex-col mt-2 flex-1">
            <p>
                {{ title }}
            </p>

            <div class="flex justify-between mt-2">
                <b class="flex-1">{{price}} ₽</b>
                <img src="/img/elements/delete-filled-svgrepo-com.svg" alt="Remove" class="remove_button" @click="Remove">
            </div>
        </div>
    </div>
</template>

<style>
.icon {
    width: 92px;
    height: 92px;
}

.remove_button {
    width: 32px;
    height: 32px;
    opacity: 50%;
    cursor: pointer;
}

.remove_button:hover {
    opacity: 100%;
}
</style>