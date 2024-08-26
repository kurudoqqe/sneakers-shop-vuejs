<script setup>
  import Card from  "./Card.vue"
  import { computed } from 'vue'

  const props = defineProps({
    items: Array,
    filter: String,
    search: String,
  })
  const sortedItems = computed(() => {
    const sortedItems = props.items.slice(0).filter((item) => {
      if (item.title.includes(props.search)) {
        return item
      }
      else {
        return false
      }
    })
    switch (props.filter) {
      case 'Default':
        return sortedItems
      case 'Increasing':
        return sortedItems.sort((a, b) => a.price - b.price)
      case 'Descending':
        return sortedItems.sort((a, b) => b.price - a.price)
    }

  })

</script>

<template>
  <div class="grid grid-cols-4 gap-5">
    <Card
      v-for="card in sortedItems"
      :key="card.id"
      :imageUrl="card.imageUrl"
      :price="card.price"
      :title="card.title"
    />
  </div>
</template>