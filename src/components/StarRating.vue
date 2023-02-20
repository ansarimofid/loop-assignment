<template>
  <div class="flex gap-x-2 cursor-pointer">
    <IconStar class="w-6" :key="index" v-for="index in rating"  iconClass="fill-orange-400"/>
    <IconStar class="w-6" :key="index" v-for="index in (allStars-rating)"  iconClass="fill-orange-200"/>
  </div>
</template>

<script>

import IconStar from './icons/IconStar.vue';

export default {
  name: "Star Rating",
  components:{
    IconStar
  },
  data() {
    return {
      allStars: 5
    }
  },
  props: {
    rating: {
      type: Number,
      default: 4
    }
  },
}
</script>

<style lang="scss" scoped>

</style>