<template>
    <div>
      <main>
        <div>
          <input type="text" 
          class=" border-2  border-blue-900 rounded-3xl p-2 search-bar" 
          placeholder="city name..."          
          v-model="query"
          @keypress="fetchWeather"
          style="max-width: 600px;"
          />
        </div>
  
        <div class="weather-wrap" v-if="typeof weather.main != 'undefined'">
          <div class="location-box">
            <div class="location">{{ weather.name }}, {{ weather.sys.country }}</div>
            <div class="date">{{ dateBuilder() }}</div>
          </div>

          <div class="weather-box">
            <div class="temp">{{ Math.round(weather.main.temp) }} °C</div>
            <div class="weather">{{ weather.weather[0].main }}</div>
          </div>
        </div>
      </main>
    </div>  
    <flex></flex>
</template>


<script >
import  {url_base,api_key,getData}  from "../components/weather";
import flex from "../../vue-flux-dev/src/components/FluxButton.vue";

export default {
  components: {
        flex
      },
    data () {
      return {
        url_base,
        api_key,
        query: '',
        weather: {},
        getData
      }
    },
    methods: {
      fetchWeather(e){
        if (e.key == "Enter"){
          fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
          .then(res => {
            return res.json();
          }).then(this.setResults);
        }
      },
      setResults (results){
        this.weather = results;
      },
      dateBuilder () {
        let d = new Date(new Date().toLocaleString('en', {timeZone: 'Asia/Tehran'}));
        let options = {   year: 'numeric',day: 'numeric', month: 'long',};
        let today = new Date().toLocaleDateString('fa-IR', options);

          let days = ["یکشنبه", "دوشنبه", "سه شنبه", "چهارشنبه", "پنجشنبه", "جمعه", 
          "شنبه" ];

          let day = days[d.getDay()];
          let year = [today];

          return `${day} ${year}`
      }
    }
  }
</script>
