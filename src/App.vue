<script setup>
import HeaderNav from './components/HeaderNav.vue'
import ProductMarketList from './components/PrductMarketList.vue'
import axios from 'axios';
import DrawerCard from './components/DrawerCard.vue';
import { onMounted, provide, ref, watch } from 'vue';
const items = ref([])
const cart = ref([])
const typeQuery = ref()
const query = ref()
const isCartOpen = ref(false)

const closeCartWindow = ()  => {
    isCartOpen.value = false;
}

const openCartWindow = ()  => {
    isCartOpen.value = true;
}

const addToCart = (item) => {
  if (!item.isAdded) {
    cart.value.push(item)
    item.isAdded = true;
  }

  else {
    cart.value.splice(cart.value.indexOf(item), 1)
    item.isAdded = false;
  }

  console.log(cart.value);
}

const removeFromCart = (item) => {
  cart.value.splice(cart.value.indexOf(item), 1)
  item.isAdded = false;
}

const clearCart = () => {
  cart.value.splice(0, cart.value.length);
  items.value.forEach(item => {
    item.isAdded = false;
  });

  alert("Заказ оформлен")
};


const calculateTotalPrice = () => {
  return cart.value.reduce((total, item) => {
    return item.isDiscount ? total + item.priceDiscount : total + item.price;
  }, 0);
};
onMounted( async() => {
  try {
    const {data} = await axios.get("https://c59c203ebe189dcf.mokky.dev/items")
    items.value = data;
  } catch (error) {
    console.log(error);
  }
});

provide("cartActions", {
    closeCartWindow,
    openCartWindow,
    removeFromCart,
    addToCart,
    calculateTotalPrice,
    clearCart
})
provide("cart", {
    cart
})
watch(typeQuery, async () => {
  try {
    const url = typeQuery.value == "" ? "https://c59c203ebe189dcf.mokky.dev/items" : "https://c59c203ebe189dcf.mokky.dev/items?type=" + typeQuery.value;
    const {data} = await axios.get(url)
    items.value = data;
  } catch (error) {
    console.log(error);
  }
})

watch(query, async () => {
  try {
    let url = query.value == "" ? "https://c59c203ebe189dcf.mokky.dev/items" : "https://c59c203ebe189dcf.mokky.dev/items?title=*" + query.value + "*";
    const {data} = await axios.get(url)
    items.value = data;
  } catch (error) {
    console.log(error);
  }
})
const onChangeSelect = (event) => {
    typeQuery.value = event.target.value;
}
const onChangeFind = (event) => {
    query.value = event.target.value;
}
</script>
<template>
   <DrawerCard v-if="isCartOpen"/>
  <div class="bg-black w-4/5 m-auto rounded-xl shadow-xl mt-14">
    <HeaderNav @openCartWindow="openCartWindow">

    </HeaderNav>
    <div class="p-10">
      <div class="flex justify-between items-center">
        <h1 class="main_label mb-8 ">Все товары</h1>
        <div class="relative">
          <select @change="onChangeSelect" class="py-2 px-3 outline-none border rounded-md find bg-black types">
          <option value="">Все</option>
          <option value="CPU">CPU</option>
          <option value="RAM">RAM</option>
        </select>
          <input @input="onChangeFind" type="text" placeholder="Поиск..." class="border rounded-md py-2 pl-10 pr-4 outline-none focus:border-yellow-400 bg-black find transition">
        </div>
      </div>

    </div>
      <ProductMarketList :items="items">

      </ProductMarketList>
  </div>
</template>

<style>
.main_label {
  color: white;
  font-weight: bold;
  font-size: 72px;
}

.find {
  color: white;
  border-radius: 10px;
}

.types {
  margin-right: 5px;
}
</style>
