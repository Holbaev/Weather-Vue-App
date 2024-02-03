<template>
  <div className="footer">
    <h3 className="footer_title">Now</h3>
    <div v-if="info !== null" className="footer_content">
      <div className="content">
        <p className="content_desk">Chance of Rain</p>
        <p className="footr_text">{{info.clouds.all}}%</p>
      </div>
      <div className="content">
        <p className="content_desk">Humidity</p>
        <p className="footr_text">{{ info.main.humidity }} %</p>
      </div>
      <div className="content">
        <p className="content_desk">Wind Speed</p>
        <p className="footr_text">{{ info.wind.speed }} k/h</p>
      </div>
      <div className="content">
        <p className="content_desk">Visiblity</p>
        <p className="footr_text">{{ info.visibility }} km</p>
      </div>
      <div className="content">
        <p className="content_desk">Pressure</p>
        <p className="footr_text">{{ info.main.pressure }} hPa</p>
      </div>
    </div>

    <div v-else className="footer_content">
      <div className="content">
        <p className="content_desk">Chance of Rain</p>
        <p className="footr_text">0%</p>
      </div>
      <div className="content">
        <p className="content_desk">Humidity</p>
        <p className="footr_text">0%</p>
      </div>
      <div className="content">
        <p className="content_desk">Wind Speed</p>
        <p className="footr_text">0 k/h</p>
      </div>
      <div className="content">
        <p className="content_desk">Visiblity</p>
        <p className="footr_text">0 km</p>
      </div>
      <div className="content">
        <p className="content_desk">Pressure</p>
        <p className="footr_text">0 hPa</p>
      </div>
    </div>
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
};
</script>

<style scoped>
.footer {
  background: #343a40;
  width: 100%;
  padding: 55px 130px;
  position: relative;
}
.footer_title {
  font-weight: 700;
  font-size: 18px;
  color: #fff;
  position: absolute;
  top: 22px;
  left: 15px;
}
.footer_content {
  display: flex;
  align-content: center;
  justify-content: space-between;
  width: 100%;
  flex-wrap: wrap;
}
.content {
  display: flex;
  align-content: center;
  justify-content: center;
  flex-direction: column;
  gap: 15px;
}
.content_desk {
  font-weight: 400;
  font-size: 18px;
  color: rgba(255, 255, 255, 0.8);
}
.footr_text {
  font-weight: 700;
  font-size: 24px;
  color: #fff;
}
@media (max-width: 800px) {
  .footer{
    padding: 50px 30px 20px;
  }
  .footer_title{
    top: 10px;
    left: 10px;
  }
}
@media (max-width: 500px) {
  .header_weaher{
    display: none;
  }
  .header{
    display: flex;
    flex-direction: column;
    width: 100%;
    gap: 15px;
  }
  .header_form{
    width: 100%;
  }
  .footer_content{
    gap: 20px;
  }
}
</style>
