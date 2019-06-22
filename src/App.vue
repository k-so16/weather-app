<template>
  <div id="app">
    <weather-component/>
  </div>
</template>

<script>
import request from 'request-promise'
import xml2js from 'xml2js'

import WeatherComponent from './components/WeatherComponent'

export default {
  name: 'app',
  data() {
    return {
      prefs: [],
    }
  },

  components: {
    WeatherComponent,
  },

  created() {
    request('http://weather.livedoor.com/forecast/rss/primary_area.xml').then(body => {
      xml2js.parseString(body, (err, data) => {
        this.prefs = data.rss.channel[0]['ldWeather:source'][0].pref
      })
    })
  },
}
</script>

<style>
/* お好みソースでどうぞ */

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
