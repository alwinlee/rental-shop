<template>
  <div class="income">
    <h3> {{ title }} </h3>
    <p> {{ rental }} x {{ fee }} = {{ rental * fee}}</p>
    <button v-on:click="resetbike">Reset Bike</button>
  </div>
</template>

<script>
export default {
  name: 'TotalIncome',
  props: {
    title: String,
    fee: Number,
    rental: Number,
  },
  data() {
    return {
    }
  },
  computed: {

  },
  methods: {
    resetbike() {
      this.$emit('resetBike', 100)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .income {
    margin: 15px 20px;
  }
  .income > h1 {
    color: #42b983;
  }

</style>
