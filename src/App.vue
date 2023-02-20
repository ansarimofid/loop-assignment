<template>
  <header>

    <main class="bg-gray-100 flex w-full min-h-screen">
      <Sidebar @updateRating="updateRating" class="w-[400px] bg-white min-h-full h-screen overflow-y-auto flex-shrink-0 sticky top-0" />
      <ResultView :allData="filteredData" class="w-full" />
    </main>
  </header>

  <main>

  </main>
</template>

<script>
import ResultView from './view/ResultView.vue';
import Sidebar from './components/Sidebar.vue';
import dummyData from "../src/global/data"

export default {
  name:"App",
  components: {
    ResultView,
    Sidebar
  },
  data() {
    return {
      dummyData,
      filters:{
        rating:[]
      }
    }
  },
  computed: {
    filteredData() {

      if(this.filters.rating.length) {
        let minRating = Math.min(...this.filters.rating)-1
        let maxRating = Math.max(...this.filters.rating)

        console.log(minRating, maxRating)

        return this.dummyData.filter(d=>parseInt(d.avg_rating) > minRating && parseInt(d.avg_rating) <= maxRating)
      }
        
      return this.dummyData
    }
  },
  methods: {
    updateRating(data) {
      this.filters.rating = data;
    }
  },
  watch: {
    'filters.rating': {
      handler:function(newValue) {
        console.log("filter changed", newValue)
      },
      deep: true
    }
  },
}

</script>


<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
