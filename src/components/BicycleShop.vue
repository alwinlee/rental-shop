<template>
  <div class="shop">
    <h1>{{ title }}</h1>
  </div>
</template>

<script>
export default {
  name: 'BicycleShop',
  props: {
    title: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.shop > h1 {
  color: #42b983;
}
</style>
