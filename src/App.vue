<template>
  <BicycleShop title="福克斯自行車店" v-bind:maxbikes="maxbikes" @rentBike="rentBike" @retuenBike="retuenBike"/>
  <TotalIncome title="Total Income" v-bind:rental="rental" v-bind:fee="fee" @resetBike="resetBike" />
</template>

<script>
import BicycleShop from './components/BicycleShop.vue'
import TotalIncome from './components/TotalIncome.vue'

export default {
  name: 'App',
  components: {
    BicycleShop, TotalIncome
  },
  data() {
    return {
      fee: 100,
      maxbikes: 20,
      rental: 0
    }
  },
  methods: {
    resetBike(e) {
      this.maxbikes = e
    },
    rentBike(e) {
      this.rental += e
      //alert(this.rental)
    },
    retuenBike() {

    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: auto;
  margin-top: 60px;
  width: 400px;
}
</style>
