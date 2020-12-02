<template>
  <div id="app">
    <h1>Coronavirus i Danmark</h1>
    <p>Tilfælde: {{ data.cases }}</p>
    <p>Tilfælde i dag: {{ data.todayCases }}</p>
    <p>Befolkning: {{ data.population }}</p>
    <p>Døde i alt: {{ data.deaths }}</p>
    <p>Døde i dag: {{ data.todayDeaths }}</p>
    <p>Genvundet helbred: {{ data.recovered }}</p>
    <p>Kritisk tilstand: {{ data.critical }}</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      data: {},
    };
  },
  name: "App",
  components: {},

  created() {
    axios
      .get(`https://corona.lmao.ninja/v3/covid-19/countries/denmark`)
      .then((res) => (this.data = res.data))
      .catch((err) => console.log(err));
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
* {
  background: black;
}

p {
  font-size: 24px;
  color: white;
  padding:5px;
}
h1 {
  color: white;
}
</style>
