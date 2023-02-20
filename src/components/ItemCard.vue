<template>
  <div class="bg-white p-6">
    <h3 class="text-xl font-bold">{{ data.chain }}</h3>
    <p class="text-gray-500 text-sm">{{ data.itemName }}/{{ data.category }}</p>
    <img class="mt-4" :src="data.Itemurl" alt="">
    
    <div class="text-sm mt-4">
      <div class="w-full flex justify-between">
        <div>Error Rate</div>
        <div>{{ getFormattedNumber(data.error_rate, 1) }}%</div>
      </div>

      <div class="w-full flex justify-between mt-2">
        <div>Dispatch</div>
        <div>{{ parseFloat(data.dispatch_time).toFixed(2) }}min</div>
      </div>

      <div class="w-full flex justify-between mt-2">
        <div>Order value</div>
        <div>${{ parseFloat(data.total_order_value).toFixed(0) }}</div>
      </div>

      <div class="w-full flex justify-between mt-2">
        <div>Order volume</div>
        <div>{{ data.total_num_of_orders }}</div>
      </div>

      <div class="w-full flex justify-between mt-2">
        <div>Retention</div>
        <div>{{ getFormattedNumber(data.store_item_retention_rate, 1) }}%</div>
      </div>
      
      <div class="w-full flex justify-between mt-2">
        <div>Rating</div>
        <div>{{ getFormattedNumber(data.avg_rating, 1) }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ItemCard",
  props: {
    data: {
      type: Object,
      default: () => { }
    }
  },
  methods: {
    getFormattedNumber(num, decimalPlaced) {
      return parseFloat(num).toFixed(decimalPlaced)
    }
  },
}
</script>

<style lang="scss" scoped></style>