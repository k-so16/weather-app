<template>
  <div id="app">
    <http-cat-component/>
  </div>
</template>

<script>
import request from 'request-promise'
import xml2js from 'xml2js'

import HttpCatComponent from './components/HttpCatComponent'

export default {
  name: 'app',
  data() {
    return {
      prefs: [],
    }
  },

  components: {
    HttpCatComponent,
  },

  created() {
    request('http://weather.livedoor.com/forecast/rss/primary_area.xml').then(body => {
      xml2js.parseString(body, (err, data) => {
        console.log(data)
        this.prefs = data.rss.channel[0]['ldWeather:source'][0].pref
        console.log('areas', this.prefs)
      })
    })
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
