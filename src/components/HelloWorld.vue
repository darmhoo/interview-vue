<script>
import axios from 'axios';
export default {
  data() {
    return {
      key: "a6e5ec0565d247b48e9114706242406",
      weatherData: null,
      baseApi: "http://api.weatherapi.com/v1"
    }
  },
  methods: {
    async getWeatherData() {
      let res = await axios.get(`${this.baseApi}/forecase.json?key=${this.key}`);
      console.log(res);
    }
  },

  mounted(){
    this.getWeatherData();
  }
}

</script>

<template>
  <div class="greetings">

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
