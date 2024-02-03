<template>
  <div >
    <HeaderVue :notify="notify" :getWeather="getWeather"/>
    <WeatherVue :info="info"/>
    <FooterVue :info="info"/>
  </div>
</template>

<script>
import axios from "axios";
  import HeaderVue from './components/Header.vue';
import WeatherVue from './components/Weather.vue';
import FooterVue from './components/Footer.vue';
export default {
  components:{
    HeaderVue,
    WeatherVue,
    FooterVue
  },
  
  data() {
    return {
      notify: "",
      info: null,
    };
  },
  methods: {
    async getWeather(city) {
      try {
        const response = await axios.get(
          `https://api.openweathermap.org/data/2.5/weather?q=${city}&units=metric&appid=691235249ab9a994cdfbb37aa667b0d6`
        );
        this.info = response.data;
        this.notify = "";
      } catch (err) {
        if (err.response.status === 404) {
          this.notify = "Город не найден";
        }
      }
    },
  },
};
</script>

<style scoped>
.app{
  background: #FFFFFF;
}
</style>