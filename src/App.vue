<template>
  <link rel="stylesheet" 
    href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css" 
    integrity="sha512-iBBXm8fW90+nuLcSKlbmrPcLa0OT92xO1BIsZ+ywDWZCvqsWgccV3gFoRBv0z+8dLJgyAHIhR35VZc2oM/gI1w==" 
    crossorigin="anonymous" 
  />
  <div id="container" :class="containerTemperature">
    <h1>BetterWeather</h1>
    <main id="app" :class="appTemperature">
        <div class="search-box">
          <input 
            type="text" 
            class="search-bar" 
            placeholder="Search..."
            v-model="query"
            @keypress="fetchWeather" 
          />
          <i class="fas fa-search" v-on:click="fetchWeather"></i>
        </div>

        <div class="weather-wrap" v-if="typeof weather.main != 'undefined'">
          <div class="location-box">
            <div class="location">{{ weather.name }}, {{ weather.sys.country }}</div>
            <div class="date">{{ dateBuilder() }}</div>
          </div>
          <div class="weather-box">
            <div id="temp" :class="tempBackground">{{ Math.round(weather.main.temp) }}°c</div>
            <div class="weather">{{ weather.weather[0].main }}</div>
            <div class="min">MIN <br> {{ Math.round(weather.main.temp_min) }}°c</div>
            <div class="max">MAX <br> {{ Math.round(weather.main.temp_max) }}°c</div>
          </div>
        </div>
        
        <div v-if="weather.weather !== undefined">
          <CloudsAnimation v-if="weather.weather[0].main=='Clouds'">
          </CloudsAnimation>

          <SunAnimation v-else-if="weather.weather[0].main=='Clear'">
          </SunAnimation>

          <RainAnimation v-else-if="weather.weather[0].main=='Rain'">
          </RainAnimation>
        </div>

        
    </main>
  </div>
</template>

<script>
import CloudsAnimation from "./components/CloudsAnimation"
import SunAnimation from "./components/SunAnimation"
import RainAnimation from "./components/RainAnimation"

export default {
  name: 'App',
  components: { 
    CloudsAnimation, 
    SunAnimation,
    RainAnimation
    },
  data () {
    return {
      api_key: '08f1525958fbc6584f628b6dac25a906',
      url_base: 'https://api.openweathermap.org/data/2.5/',
      query: '',
      weather: {}
    }
  },
  computed: {
    containerTemperature: function () {
    return {
      'warm-container': typeof this.weather.main != 'undefined' && this.weather.main.temp > 20,
      'cold-container': typeof this.weather.main != 'undefined' && this.weather.main.temp < 9
    }
  }, appTemperature: function () {
    return {
      'warm': typeof this.weather.main != 'undefined' && this.weather.main.temp > 20,
      'cold': typeof this.weather.main != 'undefined' && this.weather.main.temp < 9
    }
  }, tempBackground: function () {
    return {
      'temp-warm': typeof this.weather.main != 'undefined' && this.weather.main.temp > 20,
      'temp-cold': typeof this.weather.main != 'undefined' && this.weather.main.temp < 9
    }
  }
  },
  methods: {
    fetchWeather (e) {
      if (e.key == "Enter") {
        
        fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
          .then(res => {
            return res.json();
          }).then(this.setResults)
          .then(this.query = "");
      } 
    },
    setResults (results) {
      this.weather = results;
    },
    dateBuilder () {
      let d = new Date();
      let months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
      let days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];

      let day = days[d.getDay()];
      let date = d.getDate();
      let month = months[d.getMonth()];
      let year = d.getFullYear();

      return `${day} ${date} ${month} ${year}`;
    }
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Ubuntu:wght@300,900&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Rajdhani:wght@300&display=swap');


* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;

  body {
    font-family: 'Ubuntu', sans-serif;

    #container {
      position: relative;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      height: 100vh;
      background: rgb(167,207,242);
      background: linear-gradient(to bottom, #BDF2F2 0%, #34A6BF 50%, #074E8C 100%);

      h1 {
        position: absolute;
        top: 5vh;
        color: white;
        text-shadow: 1px 3px 2px rgba(0, 0, 0, 0.25);
        font-style: oblique;
        text-align: center;
        font-family: 'Rajdhani'
      }

      #app {
      background-image: url('./assets/cold.jpg');
      background-size: cover;
      background-position: bottom;
      transition: 0.4s;
      width: 350px;
      height: 500px;
      border-radius: 20px;
      box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
      position: relative;
      overflow: hidden;
      }

      @media screen and (max-width: 600px) {
        #app {
          width: 325px;
        }
      }

      #app.warm {
        background-image: url('./assets/warm.jpg')
      }

      #app.cold {
        background-image: url('./assets/coldd.jpg')
      }

      main {
        height: 100vh;
        padding: 25px;
        background-image: linear-gradient(to bottom, rgba(0,0,0,0.25), rgba(0,0,0,0.75))
      }

      .search-box {
        width: 100%;
        margin-bottom: 30px;
        position: relative;

        .search-bar {
          display: block;
          width: 100%;
          padding: 15px;
          color: #313131;
          font-size: 20px;
          appearance: none;
          border: none;
          outline: none;
          background: none;
          box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
          background-color: rgba(255, 255, 255, 0.5);
          border-radius: 12px;
          transition: 0.4s;
        }

        i {
          position: absolute;
          color: #313131;
          top: 35%;
          right: 6%;

          &:hover {
            cursor: pointer;
          }
        }
      }

      .search-box .search-bar:focus {
        box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
        background-color: rgba(255, 255, 255, 0.75);
      }

      .location-box .location {
        color: white;
        font-size: 32px;
        text-align: center;
        text-shadow: 1px 2px 2px rgba(0, 0, 0, 0.4);
      }

      .location-box .date {
        color: white;
        font-size: 20px;
        font-style: italic;
        text-align: center;
        text-shadow: 1px 2px 2px rgba(0, 0, 0, 0.4);
      }

      .weather-box {
        text-align: center;
        z-index: 50000;

        .min, .max {
          position: absolute;
          color: white;
          font-weight: bold;
          bottom: 32px;
          font-size: 1.2rem;
          z-index: 400;
          text-shadow: 0 0 2px black;
        }

        .min {
          left: 28px;
        }

        .max {
          right: 28px;
        }
      }

      .weather-box #temp {
        display: inline-block;
        padding: 8px 20px;
        color: white;
        font-size: 82px;
        font-weight: 900;
        text-shadow: 3px 6px rgba(0, 0, 0, 0.4);
        background-color: rgba(52, 166, 191, 0.5);
        border-radius: 16px;
        margin: 30px 0px;
        box-shadow: 3px 6px rgba(0, 0, 0, 0.4);
      }

      #temp.temp-cold {
        background-color: rgba(180, 183, 191, 0.4);
      }

      #temp.temp-warm {
        background-color: rgba(242,82,170,0.5);
      }

      .weather-box .weather {
        color: white;
        font-size: 42px;
        font-weight: 700;
        font-style: italic;
        text-shadow: 3px 6px 1px rgba(0, 0, 0, 0.25);
        z-index: 1000;
      }
    }
    #container.warm-container{
        background: rgb(242,160,160);
        background: linear-gradient(to bottom right, rgba(242,160,160,1) 0%, rgba(242,82,170,1) 50%, rgba(34,32,89,1) 100%); 
      }
    #container.cold-container {
        background: #D9D9D9;
        background: linear-gradient(to bottom left, #f0efef 0%, #B4B7BF 50%, #909197 100%);
      }
  }
}

</style>
