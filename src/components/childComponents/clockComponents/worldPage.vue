<template>
    <div class="mainer">
      <div class="tavi">
        <button>Edit</button>
        <img src="../../../assets/Clock/plus.png" alt="" />
      </div>
      <h2>World Clock</h2>
      <div class="weli">
        <h2>{{ city }}</h2>
        <h2>{{ dro }}</h2>
      </div>
    </div>
    
  </template>
  
  <script>
  export default {
    data() {
      return {
        city: "Loading...",
        time: "",
        dro: "",
      };
    },
    created() {
      this.qalaqi();
      this.refreshTime();
      this.currentTime();
    },
    methods: {
      refreshTime() {
        setInterval(() => {
          this.currentTime();
        }, 5000);
      },
      currentTime() {
        let date = new Date();
        let hh = date.getHours();
        let mm = date.getMinutes();
  
        if (hh === 0) {
          hh = 12;
        }
        if (hh > 12) {
          hh = hh - 12;
        }
  
        hh = hh < 10 ? "0" + hh : hh;
        mm = mm < 10 ? "0" + mm : mm;
  
        let time = hh + ":" + mm;
  
        this.dro = time;
      },
      qalaqi() {
        if (navigator.geolocation) {
          navigator.geolocation.getCurrentPosition(async (position) => {
            const lat = position.coords.latitude;
            const lng = position.coords.longitude;
            const response = await fetch(
              `https://nominatim.openstreetmap.org/reverse?format=jsonv2&lat=${lat}&lon=${lng}`
            );
            const data = await response.json();
            const city =
              data.address.town || data.address.city || data.address.village;
            this.city = city;
          });
        } else {
          console.error("Geolocation is not supported by this browser.");
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .weli {
    height: 80px;
    width: 108%;
    border-top: solid #3b3b3b 1px;
    border-bottom: solid #3b3b3b 1px;
    display: flex;
    justify-content: space-between;
  }
  .weli h2:first-child {
    position: relative;
    top: 20px;
  }
  .weli h2:nth-child(2) {
    position: relative;
    right: 10px;
    font-size: 45px;
    font-family: monospace;
    top: 10px;
  }
  .mainer {
    margin: 7%;
    height: 450px;
  }
  .tavi {
    display: flex;
    justify-content: space-between;
    width: 100%;
  }
  .tavi img {
    height: 22px;
  }
  .tavi button {
    background: none;
    color: orange;
    position: relative;
    right: 8px;
  }
  </style>
  