<template>
  <div>
    <div id="searchbar" class="row">
      <b-form-input
        v-model.lazy="city"
        aria-describedby="input-live-help input-live-feedback"
        placeholder="Search cities..."
        v-on:keyup.enter="search"
      ></b-form-input>
      <button class="noselect" @click="search">Search</button>
    </div>
    <div>
      <b-card id="card" img-src="" img-top tag="article" class="mb-2">
        <div class="row">
          <Sun v-show="weather.description == 'clear sky'" />
          <CloudSun v-show="weather.description == 'broken clouds'" />
          <Rain v-show="weather.main == 'Rain'" />
          <Rain v-show="weather.main == 'Thunderstorm'" />
          <Snow v-show="weather.main == 'Snow'" />
          <Cloud v-show="weather.main == 'Clouds'" />
          <Rain v-show="weather.main == 'Drizzle'" />

          <h1 id="celcius">{{ weather.temprature }}°C</h1>
        </div>
        <br /><br />
        <div class="row">
          <h1 style="margin-left: 10px">{{ weather.cityName }}</h1>
          <h1 style="margin-left: 30px">{{ weather.country }}</h1>
        </div>

        <hr />

        <b-card-text> {{ weather.description }} </b-card-text>
        <div>
          <div class="row">
            <h3 style="margin-left: auto; margin-right: auto">
              Today
              <img
                :src="
                  'http://openweathermap.org/img/wn/' + weather.icon + '.png'
                "
              />
            </h3>
          </div>

          <h4>Min: {{ weather.min }}</h4>
          <h4>Max: {{ weather.max }}</h4>
        </div>
      </b-card>
    </div>
  </div>
</template>

<script>
import Sun from "./Weather/Sun.vue";
import Cloud from "./Weather/Cloud.vue";
import Rain from "./Weather/Rain.vue";
import Snow from "./Weather/Snow.vue";
import CloudSun from "./Weather/CloudSun.vue";
export default {
  data() {
    return {
      city: "",
      iconUrl: "https://openweathermap.org/img/w/",
      weather: {
        cityName: "",
        temprature: "",
        country: "",
        description: "",
        main: "",
        min: "",
        max: "",
        icon: "",
      },
      apikey: "d455992c154b750edc0787c95ed52fbd",
    };
  },
  components: {
    Sun: Sun,
    Cloud: Cloud,
    Rain: Rain,
    Snow: Snow,
    CloudSun: CloudSun,
  },
  methods: {
    search() {
      console.log(this.city);
      let url = `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=${this.apikey}&units=metric`;
      fetch(url)
        .then((res) => {
          return res.json();
        })
        .then((data) => {
          console.log(data);
          this.weather.cityName = data.name;
          this.weather.temprature = Math.ceil(data.main.temp);
          this.weather.country = data.sys.country;
          this.weather.description = data.weather[0].description;
          this.weather.main = data.weather[0].main;
          this.weather.max = Math.ceil(data.main.temp_max);
          this.weather.min = Math.ceil(data.main.temp_min);
          this.weather.icon = data.weather[0].icon;
          this.city = "";
        });
    },
  },
};
</script>

<style scoped>
.card {
  background-color: rgba(255, 255, 255, 0);
  color: aliceblue;
  margin-left: auto;
  margin-right: auto;
  width: 95%;
  margin-top: 5%;
  height: auto;
  shape-image-threshold: inherit;
  background: rgba(41, 80, 220, 0.05);
  box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
  backdrop-filter: blur(1.5px);
  -webkit-backdrop-filter: blur(1.5px);
  border-radius: 10px;
  border: 1px solid rgba(255, 255, 255, 0.18);
}
#celcius {
  margin-left: auto;
  margin-right: 0;
}
#searchbar {
  padding: 40px;
  margin-left: 3%;
}
#searchbar input {
  width: 70%;
  background: rgba(255, 255, 255, 0.25);
  box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(4px);
  color: white;
}
#searchbar ::placeholder {
  color: rgba(255, 255, 255, 0.904);
  font-weight: 100;
}
.noselect {
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  -webkit-tap-highlight-color: transparent;
}
button {
  width: 25%;
  height: 38px;
  margin-left: 10px;
  cursor: pointer;
  border: none;
  font-family: "Comfortaa", cursive;
  color: rgba(255, 255, 255, 0.692);
  font-size: 15px;
  border-radius: 4px;
  box-shadow: inset 0px 3px 5px rgba(255, 255, 255, 0.5),
    0px 0px 10px rgba(0, 0, 0, 0.15);
  background: rgb(2, 0, 36);
  background: linear-gradient(
    45deg,
    rgba(2, 0, 36, 0) 5%,
    rgba(255, 255, 255, 0.5) 6%,
    rgba(255, 255, 255, 0) 9%,
    rgba(255, 255, 255, 0.5) 10%,
    rgba(255, 255, 255, 0) 17%,
    rgba(255, 255, 255, 0.5) 19%,
    rgba(255, 255, 255, 0) 21%
  );
  background-size: 150%;
  background-position: right;
  transition: 1s;
}
button:hover {
  background-position: left;
  color: white;
  box-shadow: inset 0px 3px 5px rgba(255, 255, 255, 1),
    0px 0px 10px rgba(0, 0, 0, 0.25);
}
button:focus {
  outline: none;
}
</style>