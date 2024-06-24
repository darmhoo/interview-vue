<script>
import axios from 'axios';
import TempChart from './TempChart.vue';
export default {
  data() {
    return {
      key: "a6e5ec0565d247b48e9114706242406",
      currentWeatherData: null,
      foreCast: null,

      baseApi: "http://api.weatherapi.com/v1"
    }
  },
  methods: {
    async getWeatherData() {
      let res = await axios.get(`${this.baseApi}/forecast.json?key=${this.key}&q=Lagos`);
      this.currentWeatherData = res.data;
    },

    async getWeatherForecast() {
      let res = await axios.get(`${this.baseApi}/forecast.json?key=${this.key}&q=Lagos&days=14`);
      this.foreCast = res.data.forecast;
    }
  },

  mounted(){
    this.getWeatherData();
    this.getWeatherForecast();
  }
}

</script>

<template>
  <div class="">
   <h2>The Current Weather Data for Lagos Today</h2>
   <div>
    <p>
      <span>Cloud: </span> <span> {{ currentWeatherData?.current?.cloud }}</span><br>
      <span>Condition: </span> <span> {{ currentWeatherData?.current?.condition.text }}</span> <span> <img :src="currentWeatherData?.current?.condition.icon" alt=""></span><br>
      <span>Dew Point: </span> <span> {{ currentWeatherData?.current?.dewpoint_c }}</span><br>
      <span>Pressure: </span> <span> {{ currentWeatherData?.current?.pressure_in }}</span><br>

    </p>
   </div>

   <div>
    <TempChart></TempChart>
   </div>


  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {

  .greetings h1,
  .greetings h3 {
    display: block;
    text-align: left;
  }
}
</style>
