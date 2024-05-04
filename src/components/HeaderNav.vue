
<script setup>
import {defineEmits} from 'vue'
const emit = defineEmits(["openCartWindow"]);
</script>
<template>
    <header class="flex justify-between border-b ">
      <div class="flex items-center gap-4">
        <img src="/img/header_icon.png" alt="Logo" class="w-25">
        <div>
          <h2 class="label text-xl font-bold">Магазин Макси | Магазин комплектующих</h2>
          <p class="sub_label">
            Лучшие предложения
          </p>
        </div>
      </div>
      <ul class="flex items-center gap-10">
        <li class="flex items-center gap-3 options">    
          <a href="#" class="button-options" @click="() => emit('openCartWindow')">Корзина</a>
          <a href="#" class="button-options">Профиль</a>
          

        </li>
      </ul>
    </header>
</template>

<style>
  .label {
    color: white
    
  }

  .sub_label {
    color: rgb(255, 255, 255)
  }

  .options {
    margin-right: 20px;
  }

  .button-options {
	background-color:#e8da58;
	border-radius:28px;
	display:inline-block;
	cursor:pointer;
	color:#000000;
	font-family:Arial;
	font-size: 20px;
	padding:16px 31px;
	text-decoration:none;
}
.button-options:hover {
	background-color:#f8e95d;
}
.button-options:active {
	position:relative;
	top:1px;
}

        
</style>