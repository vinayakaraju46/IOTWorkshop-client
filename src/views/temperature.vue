<template>
  <v-card flat>
    <v-card-text class="text-h5 mb-1"> Temperature is {{ temp }}</v-card-text>
    <v-card-text class="text-h5 mb-1"> Humidity is {{ humidity }}</v-card-text>
  </v-card>
</template>

<script>
const axios = require('axios');

export default {
    name: "temperature",
    data() {
        return {
          temp: '',
          humidity: ''
        }
    },
    mounted() {
      this.getWeather();
    },
    methods: {
      async getWeather() {
        axios.get('https://mocki.io/v1/35718433-8268-4eb6-a889-af8f595e8918')
        .then((data) => {
          this.temp = data.data.temp;
          this.humidity = data.data.humidity;
        })
      }
    }
}
</script>
