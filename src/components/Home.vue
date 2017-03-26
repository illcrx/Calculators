<template>
  <div class="home">
    <div>
      <div class="row">
        <p class="title">Initial Investment</p>
        <input type="number" v-model="initialInvestment" v-on:change="makeMoney">
      </div>
       <div class="row">
        <p class="title"> Annual Additional Investment</p>
        <input type="number" v-model="additionalInvestment" v-on:change="makeMoney">
      </div>
      <div class="row">
        <p class="title">Years to Invest</p>
        <input type="number" v-model="years" min="1" max="100" v-on:change="makeMoney">
      </div>
      <div class="row">
        <p class="title">Rate of Return % </p>
        <input type="number" v-model="rate" v-on:change="makeMoney" v-on:enter="makeMoney">
      </div>
    </div>
    <div class='results'>
      <p class="title">Total</p>
      <h2> ${{ results }} </h2>
    </div>
  </div>
  
</template>

<script>
export default {
  name: 'home',
  data: {
    message1: '',
    message2: '',
    results: 0,
    rate: 0,
    initialInvestment: 0,
    years: 0,
    additionalInvestment: 0
  },
  methods: {
    makeMoney: function () {
      let init = this.initialInvestment
      let years = this.years
      let rate = this.rate / 100
      let result

      rate = 1 + rate
      init = init * rate
      result = init

      for (let i = 1; i < years; i++) {
        result += this.additionalInvestment
        result *= rate
      }
      this.results = result.toFixed(2)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin: 0 10px;
}

a {
  color: #42b983;
}

input {
  padding: 10px;
  font-size: 1.5em;
  text-align: center;
  width: 200px;
  background: silver;
}

.title {
  font-size: 1.4em;
  font-weight: 600;
}

</style>
