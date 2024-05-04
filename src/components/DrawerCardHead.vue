<script setup>
import {inject} from 'vue'
const {closeCartWindow} = inject('cartActions')
</script>
<template>
        <div class="flex items-center gap-5 mb-5">
            <img src="/img/elements/exit-left-svgrepo-com.svg" alt="exit" class="exit_button transition" @click="closeCartWindow">
            <h2 class="font-bold text-2xl">Корзина</h2>
        </div>
</template>

<style>
.exit_button {
    width: 32px;
    height: 32px;
    cursor: pointer;
    opacity: 30%;
}

.exit_button:hover {
    opacity: 100%;
}
</style>