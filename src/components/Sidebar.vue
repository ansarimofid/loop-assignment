<template>
  <div class="py-20 px-6">
    <h2 class="font-bold text-2xl">Item performance</h2>
    <div class="mt-6 flex gap-x-2">
      <button class="text-sm uppercase px-4 py-2 whitespace-nowrap bg-cyan-50 text-cyan-600 font-medium"> Save This
        Search</button>
      <button class="text-sm uppercase px-4 py-2 whitespace-nowrap text-cyan-600"> See All Searches</button>
    </div>

    <!-- Error -->
    <div class="mt-10">
      <FilterSelector :filters="errRate" :activeFilter="'0'" title="Error Rate" />
    </div>

    <div class="mt-10">
      <div>
        <h4>Number of Orders</h4>
        <Slider tooltip-position="bottom" class="mt-4 slider-color" :min="0" :max="500" v-model="numOfOrder"
          :default="[30, 70]" />
      </div>
      <div class="mt-16">
        <h4>Order Value</h4>
        <Slider :format="(v) => (`$${parseInt(v)}`)" tooltip-position="bottom" class="mt-4 slider-color" :min="0" :max="500"
          v-model="orderValue" :default="[30, 70]" />
      </div>

      <div class="mt-16">
        <h4>Price Range</h4>
        <Slider :format="(v) => (`$${parseInt(v)}`)" tooltip-position="bottom" class="mt-4 slider-color" :min="0" :max="500"
          v-model="priceRange" :default="[30, 70]" />
      </div>
    </div>

    <div class="mt-20">
      <h4>Rating</h4>
      <div class="mt-6">
        <div :key="i" v-for="i in 5" class="flex items-center gap-x-4 mt-2 cursor-pointer">
          <input :id="`checkbox-${i}`" :value="i" v-model="checkedrating" class="accent-cyan-600" type="checkbox">
          <label :for="`checkbox-${i}`" class="flex">
            <StarRating :rating="i" />
          </label>
        </div>
      </div>
      <FilterSelector class="mt-10" :filters="pTime" :activeFilter="'0'" title="Preparation Time" />
      <FilterSelector class="mt-10" :filters="wTime" :activeFilter="'0'" title="Wait Time" />
      <FilterSelector class="mt-10" :filters="wTime" :activeFilter="'0'" title="Hands off time" />
    </div>

    <div class="mt-10">
      <h4>Basket Size</h4>
      <Slider :format="(v) => (`$${parseInt(v)}`)" tooltip-position="bottom" class="mt-4 slider-color" :min="0" :max="500"
        v-model="priceRange" :default="[30, 70]" />
    </div>
  </div>
</template>

<script>

import StarRating from './StarRating.vue';
import FilterSelector from './FilterSelector.vue';
import Slider from '@vueform/slider'

export default {
  name: "Sidebar",
  components: {
    StarRating,
    FilterSelector,
    Slider
  },
  data() {
    return {
      errRate: [
        { name: 'Under 0.5%', key: '0' },
        { name: '0.5% - 1%', key: '1' },
        { name: '1% - 1.5%', key: '2' },
        { name: '1.5% - 2%', key: '3' },
        { name: '2% - 2.5%', key: '4' },
        { name: 'Above 2.5%', key: '5' },
      ],
      pTime: [
        { name: 'Under 5 min', key: '0' },
        { name: '5 to 10 min', key: '1' },
        { name: '10 to 20 min', key: '2' },
        { name: 'Above 20 min', key: '3' },
      ],
      wTime: [
        { name: 'Under 5 min', key: '0' },
        { name: '5 to 10 min', key: '1' },
        { name: '10 to 20 min', key: '2' },
        { name: 'Above 20 min', key: '3' },
      ],
      hTime: [
        { name: 'Under 5 min', key: '0' },
        { name: '5 to 10 min', key: '1' },
        { name: '10 to 20 min', key: '2' },
        { name: 'Above 20 min', key: '3' },
      ],
      numOfOrder: [56, 423],
      orderValue: [54, 423],
      priceRange: [54, 345],
      basketSize: [54, 345],
      checkedrating: []
    }
  },
  watch: {
    checkedrating(newValue, oldValue) {
      this.$emit('updateRating', newValue)
    }
  },
}
</script>

<style>
.slider-color {
  --slider-connect-bg: #0891b2;
  --slider-tooltip-bg: #0891b2;
  --slider-handle-ring-color: #0891b2;
  --slider-handle-bg: #0891b2
}
</style>
<style src="@vueform/slider/themes/default.css"></style>