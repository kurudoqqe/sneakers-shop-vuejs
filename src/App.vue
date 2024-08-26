<script setup>
  import axios from 'axios'
  import {onMounted, ref} from 'vue'

  import Header from "./components/Header.vue"
  import CardList from "./components/CardList.vue"
  //import Drawer from  "./components/Drawer.vue"
  const selectedFilter = ref('Default')
  const seachFilter = ref('')
  const items = ref([])
  onMounted(async () => {
    try {
      const {data} = await axios.get('https://8b17068d0d2abd95.mokky.dev/items')
      items.value = data
    }
    catch (error) {
      console.error('Ошибка: ' + error)
    }
  })
</script>

<template>
  <div class="bg-white w-4/5 m-auto mt-14 rounded-xl shadow-xl">
    <Header/>
    {{seachFilter}}
    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-8">Все кроссовки</h2>
        <div class="flex gap-4">
          <select v-model="selectedFilter" class="py-2 px-3 border rounded-md outline-none cursor-pointer">
            <option selected value="Default">Без сортировки</option>
            <option value="Increasing">По цене (Возрастание)</option>
            <option value="Descending">По цене (Убывание)</option>
          </select>
          <label class="relative">
            <img src="/search.svg" alt="seach" class="absolute left-4 top-3 opacity-10 hover:opacity-40 cursor-pointer">
            <input class="border rounded-md py-2 pl-11 pr-4 outline-none focus:border-gray-400 " placeholder="Поиск..." v-model="seachFilter">
          </label>
        </div>
      </div>
      <CardList :items="items" :filter="selectedFilter" />
<!--      <Drawer/>-->
    </div>
  </div>
</template>