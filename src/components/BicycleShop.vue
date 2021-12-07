<template>
  <div class="shop">
    <h1>{{ title }}</h1>
    <img style="width: 60px" src="@/assets/bicycle-icon.png" />
    <div class="bulletin">
      <p> Available bicycles : {{ maxbikes - rentalbikes }} </p>
      <p> Rental bicycles : {{ rentalbikes}} </p>
      <div class="button-group">
        <button v-on:click="returnBike" :disabled="rentalbikes <= 0">還</button>
        <p style="display: inline-block; width: 40px;"> {{ maxbikes - rentalbikes }} </p>
        <button @click="rentBike" v-bind:disabled="(maxbikes - rentalbikes) <= 0">借</button>
      </div>

      <div class="info-msg">
        <p class="text-info" v-if="(maxbikes - rentalbikes) > 0">Bikes are available.</p>
        <p class="text-danger" v-else>No bike is available.</p>
      </div>
      <div class="info-msg">
        <p v-show="haveBikes" :class="{'text-info': haveBikes, 'text-danger': !haveBikes}">自転車が利用可能です</p>
        <p v-show="haveBikes == false" :class="{'text-info': haveBikes, 'text-danger': !haveBikes}">自転車はありません</p>
      </div>

    </div>
    <hr style="width: 20%;">
    <div class="rules">
      <h3>Rules</h3>
      <ol>
        <li v-for="(item, index) in rules" :key="index"> {{item}} </li>
      </ol>
    </div>
    <hr style="width: 20%;">
  </div>
</template>

<script>


export default {
  name: 'BicycleShop',
  props: {
    title: String,
    maxbikes: Number
  },
  data() {
    return {
      rentalbikes: 0,
      fee: 100,
      rules: ['💰 $100 each time.', 'Please return no later than 18:00 🕕.', 'Be safe 🙌🏻.']
    }
  },
  computed: {
    totalIncome() {
      return (this.rentalbikes) * this.fee;
    },
    haveBikes() {
      return (this.maxbikes - this.rentalbikes) > 0 ? true : false;
    }
  },
  methods: {
    returnBike() {
      this.rentalbikes -= 1
      this.$emit('returnBike', 1)
    },
    rentBike() {
      this.rentalbikes += 1
      this.$emit('rentBike', 1)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .shop {
    text-align: center;
  }

  .shop > h1 {
    color: #42b983;
  }

  .shop > h2:after {
    content: '🚲';
    font-weight: normal;
  }

  .bulletin {
    margin: 20px;
  }

  .text-info { color: #0d6efd; }

  .text-danger { color: #dc3545; }

  .button-group {
    /* display: flex; */
    /* align-items: center;*/
    margin: 0 auto;
    text-align: center;
  }

  .rules {
    width: 350px;
    text-align: left;
    margin: 15px auto;
  }

  .rules > h3 {
    text-align: center;
  }
</style>
