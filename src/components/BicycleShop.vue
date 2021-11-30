<template>
  <div class="shop">
    <h1>{{ title }}</h1>
    <div class="bulletin">
      <p> Number of bicycles : {{ numbers }} </p>
      <p> Total income : {{ totalIncome }} </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BicycleShop',
  props: {
    title: String
  },
  data() {
    return {
      numbers: 20,
      fee: 100
    }
  },
  computed: {
    totalIncome() {
      return this.numbers * this.fee;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .shop > h1 {
    color: #42b983;
  }

  .shop > h1:after {
    content: '🚲';
    font-weight: normal;
  }
  .bulletin {
    margin: 20px;
  }
</style>
