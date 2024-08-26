<script setup>
  import DrawerList from "./DrawerList.vue"
</script>

<template>
  <div class="fixed top-0 left-0 h-full w-full bg-black opacity-30 z-10"/>
  <div class="bg-white w-96 h-full fixed right-0 top-0 z-20 p-8 overflow-x-auto">
    <div class="flex items-center gap-5 mb-8">
      <img src="/arrow-next.svg" alt="back" class="opacity-30 cursor-pointer rotate-180 hover:opacity-100 transition hover:translate-x-1"/>
      <h2 class="text-2xl font-bold">Корзина</h2>
    </div>
    <DrawerList/>
    <div class="flex flex-col gap-3 mt-8 mb-6">
      <div class="flex gap-2">
        <span>Итого:</span>
        <div class="flex-1 border-b border-dashed"/>
        <b>12900 ₽</b>
      </div>
      <div class="flex gap-2">
        <span>Налог 5%:</span>
        <div class="flex-1 border-b border-dashed"/>
        <b>900 ₽</b>
      </div>
    </div>

    <button
      disabled=""
      class="bg-lime-300 w-full disabled:opacity-40 rounded-xl py-2 hover:shadow-xl hover:-translate-y-1 transition cursor-pointer">
      Оформить заказ
    </button>
  </div>
</template>