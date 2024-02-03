<template>
  <div>
    <div className="header">
      <div className="header_logo">
        <img src="../assets/img/Group 2.png" alt="" className="logo_img" />
      </div>
      <div class="header_form">
        <input
          type="text"
          v-model="city"
          className="form_input"
          placeholder="Введите город"
        />
        <button
          v-if="city !== ''"
          @click="getWeather(this.city)"
          className="form_search"
        >
          <svg
            width="73"
            height="40"
            viewBox="0 0 74 40"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M0.5 0H68.5C71.2614 0 73.5 2.23858 73.5 5V35C73.5 37.7614 71.2614 40 68.5 40H0.5V0Z"
              fill="#EB6F4C"
            />
            <path
              d="M41.2103 22.6361C42.2996 21.1495 42.7874 19.3063 42.5763 17.4754C42.3652 15.6444 41.4706 13.9607 40.0715 12.7611C38.6725 11.5615 36.8721 10.9345 35.0307 11.0054C33.1892 11.0764 31.4425 11.8401 30.1399 13.1439C28.8372 14.4476 28.0749 16.1951 28.0052 18.0369C27.9356 19.8787 28.5638 21.6788 29.7643 23.0772C30.9647 24.4756 32.6488 25.3691 34.4797 25.579C36.3105 25.7888 38.1531 25.2995 39.6387 24.209H39.6376C39.6713 24.254 39.7073 24.2968 39.7478 24.3384L44.0789 28.6701C44.2898 28.8812 44.576 28.9999 44.8744 29C45.1728 29.0001 45.4591 28.8816 45.6702 28.6707C45.8812 28.4597 45.9999 28.1735 46 27.8751C46.0001 27.5766 45.8817 27.2903 45.6707 27.0792L41.3396 22.7475C41.2994 22.7068 41.2562 22.6692 41.2103 22.635V22.6361ZM41.5005 18.3112C41.5005 19.1238 41.3405 19.9285 41.0295 20.6793C40.7186 21.43 40.2628 22.1122 39.6883 22.6868C39.1138 23.2615 38.4317 23.7173 37.681 24.0283C36.9303 24.3392 36.1258 24.4993 35.3132 24.4993C34.5007 24.4993 33.6961 24.3392 32.9455 24.0283C32.1948 23.7173 31.5127 23.2615 30.9382 22.6868C30.3636 22.1122 29.9079 21.43 29.5969 20.6793C29.286 19.9285 29.126 19.1238 29.126 18.3112C29.126 16.67 29.7778 15.096 30.9382 13.9355C32.0985 12.775 33.6723 12.123 35.3132 12.123C36.9542 12.123 38.528 12.775 39.6883 13.9355C40.8486 15.096 41.5005 16.67 41.5005 18.3112Z"
              fill="white"
            />
          </svg>
        </button>
        <button v-else disabled className="form_search_disabled">
          <svg
            width="73"
            height="40"
            viewBox="0 0 74 40"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M0.5 0H68.5C71.2614 0 73.5 2.23858 73.5 5V35C73.5 37.7614 71.2614 40 68.5 40H0.5V0Z"
              fill="#EB6F4C"
            />
            <path
              d="M41.2103 22.6361C42.2996 21.1495 42.7874 19.3063 42.5763 17.4754C42.3652 15.6444 41.4706 13.9607 40.0715 12.7611C38.6725 11.5615 36.8721 10.9345 35.0307 11.0054C33.1892 11.0764 31.4425 11.8401 30.1399 13.1439C28.8372 14.4476 28.0749 16.1951 28.0052 18.0369C27.9356 19.8787 28.5638 21.6788 29.7643 23.0772C30.9647 24.4756 32.6488 25.3691 34.4797 25.579C36.3105 25.7888 38.1531 25.2995 39.6387 24.209H39.6376C39.6713 24.254 39.7073 24.2968 39.7478 24.3384L44.0789 28.6701C44.2898 28.8812 44.576 28.9999 44.8744 29C45.1728 29.0001 45.4591 28.8816 45.6702 28.6707C45.8812 28.4597 45.9999 28.1735 46 27.8751C46.0001 27.5766 45.8817 27.2903 45.6707 27.0792L41.3396 22.7475C41.2994 22.7068 41.2562 22.6692 41.2103 22.635V22.6361ZM41.5005 18.3112C41.5005 19.1238 41.3405 19.9285 41.0295 20.6793C40.7186 21.43 40.2628 22.1122 39.6883 22.6868C39.1138 23.2615 38.4317 23.7173 37.681 24.0283C36.9303 24.3392 36.1258 24.4993 35.3132 24.4993C34.5007 24.4993 33.6961 24.3392 32.9455 24.0283C32.1948 23.7173 31.5127 23.2615 30.9382 22.6868C30.3636 22.1122 29.9079 21.43 29.5969 20.6793C29.286 19.9285 29.126 19.1238 29.126 18.3112C29.126 16.67 29.7778 15.096 30.9382 13.9355C32.0985 12.775 33.6723 12.123 35.3132 12.123C36.9542 12.123 38.528 12.775 39.6883 13.9355C40.8486 15.096 41.5005 16.67 41.5005 18.3112Z"
              fill="white"
            />
          </svg>
        </button>
        <div class="notify">
          <p class="notify_text">{{ notify }}</p>
        </div>
      </div>
      <div className="header_weaher">
        <p className="weaher_text">°C / °F</p>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  props: {
    notify: {
      type: String,
      required: true,
    },
    getWeather: {
      type: Function,
      required: true,
    },
  },
  data() {
    return{
      city:""
    }
  },

  methods: {
   
  },
};
</script>

<style scoped>
.header {
  background: #343a40;
  padding: 30px 105px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.header_form {
  display: flex;
  align-items: center;
  width: 40%;
  position: relative;
}
.notify {
  position: absolute;
  top: 103%;
  left: 37%;
  bottom: 0px;
}
.notify_text {
  font-weight: 400;
  font-size: 20px;
  color: #fff;
}
.form_input {
  width: 90%;
  height: 40px;
  border-radius: 5px 0 0 5px;
  padding-left: 20px;
  font-weight: 400;
  font-size: 18px;
  color: #343a40;
  border: none;
  outline: none;
}
.form_search_disabled {
  display: flex;
  align-items: center;
  cursor: not-allowed;
  height: 40px;
  border: none;
  background: transparent;
}
.form_search {
  display: flex;
  align-items: center;
  cursor: pointer;
  height: 40px;
  background: transparent;
  border: none;
}
.header_weaher {
  display: flex;
  padding: 10px 20px;
  border-radius: 5px;
  height: 40px;
  width: 140px;
  background: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
}
.weaher_text {
  font-weight: 500;
  font-size: 18px;
  text-align: center;
  color: #343a40;
}
@media (max-width: 800px) {
  .header{
    padding: 20px 30px 50px;
  }
}
@media (max-width: 500px) {
  .header_weaher{
    display: none;
  }
  .notify{
    left: 30%;
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
}
</style>
