<template>
  <div class="py-20 px-6">
    <h2 class="font-bold text-2xl">Results <span class="font-normal">({{ allData.length }} items)</span></h2>
    <div class="grid grid-cols-3 gap-6 mt-10">
      <ItemCard v-for="data in allData" :data="data" />
    </div>
  </div>
</template>

<script>
import ItemCard from '../components/ItemCard.vue';
export default {
  name: "Result View",
  components: {
    ItemCard
  },
  props: {
    allData: {
      type: Array,
      default: []
    },
  },
}
</script>

<style lang="scss" scoped></style>