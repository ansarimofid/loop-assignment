<template>
  <div>
    <h4>{{ title }}</h4>
    <div class="flex flex-wrap gap-y-3 gap-x-2 mt-4 cursor-pointer">
      <div v-for="filter in filters" class="px-3 py-2 bg-gray-50"
        :class="{ 'border-cyan-600 border': activeFilter === filter.key }">
        {{ filter.name }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FilterSelector',
  props: {
    filters: {
      type: Array,
      default: []
    },
    activeFilter: String,
    title: String
  },
}
</script>

<style lang="scss" scoped></style>