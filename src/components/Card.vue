<script setup>
  defineProps({
    imageUrl: String,
    title: String,
    price: Number
  })
</script>

<template>
  <div>
    <div class="relative bg-white border border-slate-200 rounded-3xl p-8 max-h-72 cursor-pointer transition hover:-translate-y-2 hover:shadow-xl">
      <img v-if="isFavorite" class="absolute top-6 left-6" @click="isFavorite" src="/like-2.svg" alt="like1"/>
      <img v-else class="absolute top-6 left-6" @click="isFavorite" src="/like-1.svg" alt="like1"/>
      <img :src="imageUrl" class="max-h-40" @dragstart.prevent/>
      <b>{{title}}</b>
      <div class="flex justify-between mt-1.5">
        <div>
          <span class="text-slate-400">Цена: </span>
          <b>{{price}} руб.</b>
        </div>
        <img v-if="isAdded" @click="onClickAdd" src="/checked.svg" alt="add"/>
        <img v-else @click="onClickAdd" src="/plus.svg" alt="added"/>
      </div>
    </div>
  </div>
</template>
