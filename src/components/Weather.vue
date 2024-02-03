<template>
    <div v-if="info !== null" className="weather">
        <p className="weather_city">{{info.name}}</p>
        <p className="weather_time">Нынешнее время</p>
        <h3 className="weather_degree">{{info.main.temp}} °C</h3>
    </div>
    <div v-else className="weather">
        <p>{{ info }}</p>
        <p className="weather_city">Город</p>
        <p className="weather_time">Нынешнее время</p>
        <h3 className="weather_degree">0°C</h3>
    </div>
</template>

<script>

export default {

    props:{
        info:{
            type: Object,
            required:true,
        }
    },
    methods:{
        
    }
};
</script>

<style scoped>
.weather {
    padding: 110px 105px;
    background: #fff;
}
.weather_city {
font-weight: 400;
font-size: 32px;
color:#343A40;
margin-bottom: 20px;
}
.weather_time {
font-weight: 400;
font-size: 18px;
color: rgba(52, 58, 64, 0.9);
margin-bottom: 20px;
}
.weather_degree {
font-weight: 500;
font-size: 96px;
color:#343A40;
}
@media (max-width: 800px) {
  .weather{
    padding: 100px 30px;
    align-items: center;
    display: flex;
    justify-content: center;
    flex-direction: column;
  }
  .footer_title{
    top: 10px;
    left: 10px;
  }
}
</style>