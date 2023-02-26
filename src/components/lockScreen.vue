<template>
  <div class="middle" id="middle" v-if="gatishva">
    <p>{{ dayString }}, {{ thisDay }} {{ month }}</p>
    <h1 class="clock">{{ dro }}</h1>
  </div>

  <div class="bottom" v-if="gatishvaOri">
    <button class="flash" @click="flashLight()">
      <img
        src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABkAAAAZCAYAAADE6YVjAAAACXBIWXMAAAsTAAALEwEAmpwYAAAA40lEQVR4nNXTIQxBYRSG4ctEExTh5isKiiCpmplJgiBIKlFWBNVmgmC2m9EkG9FEVVXYzHjN9ic7tv/enQ3fdsIp3xPOjuN8M0AcKAEVi8mGRfrY5wakwiBjgiX9s0g/IOKGQV5Ht80+MGCQCOBbAGcgHwoxUBRoAktg+zZrYAR4zt8EqANTYRKaSO/DPeKaSNeULoAq8DB7TBPpmNK22S/AVQ0wpS0BOWkjDYPMXj8B3IGjNlITjn7QRsoCstNGigKy0UYKArLSRnICMtdGMgLiayOegEy0EVdAhtpIUkAGtgVPCR3ICep9tNgAAAAASUVORK5CYII="
      />
    </button>
    <button @click="startCamera(), openCamera()">
      <img
        src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAAAUCAYAAACNiR0NAAAACXBIWXMAAAsTAAALEwEAmpwYAAABJUlEQVR4nNXUyypFcRTH8f0UnoGRKELJzP0ZiDrmYsTI5Q1IjCTewCWjQ4YuJbc6ZOoykJHRGXy0a506YZ9NJH71q9Va//Xd+7/WbifJvxTqcCtbaa0uq7kBBYxVuShfe296CqhPgY81ml6wjvHwRuSy9JACK7qP5krDPhoxF3Hq2cgdZBGTqngmRrCNU7TiEiNoDo/iAi04ywOWcRVxD07Qhq2qM5toxzH68oAVPaELq5j3XukI1tCJ588AzzGMidjkWxWjNhRnc4F36MUClj+oL2ER3bHIXKCYXfr0JtxU5a9jOWcxS58F7mAQh+jAQLgjcv3Y/QpQXLc9tlwKb8bbr8hQorZKsYCu8GRcWy1g2c+pnAKncRQf63d8hKnf/jP+Ab0Cf99IyLJ4H3IAAAAASUVORK5CYII="
      />
    </button>
  </div>
  <video
    style="margin-top: 40%; height: 100%; width: 100%"
    ref="videoElement"
    autoplay
  ></video>
</template>

<script>
export default {
  data() {
    return {
      day: "",
      today: new Date(),
      month: "",
      weekday: [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thrusady",
        "Friday",
        "Saturday",
      ],
      monthNames: [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December",
      ],
      dayNumber: "",
      dayString: "",
      thisDay: "",
      time: "",
      makeLight: false,
      dro: "",
      gatishva: true,
      gatishvaOri: true,
    };
  },
  created() {
    this.refreshTime();
    this.currentTime();
  },
  methods: {
    openCamera() {
      this.$emit("toggle-camera");
      this.gatishva=false;
      this.gatishvaOri = false;
    },
    startCamera() {
      this.browser = false;
      this.browserOn = false;
      this.camera = true;
      navigator.mediaDevices
        .getUserMedia({ video: true })
        .then((stream) => {
          this.$refs.videoElement.srcObject = stream;
          this.$refs.videoElement.play();
        })
        .catch((error) => {
          console.log(error);
        });
    },
    refreshTime() {
      setInterval(() => {
        this.currentTime();
      }, 5000);
    },
    flashLight() {
      this.$emit("flashLight");
    },
    currentDate() {
      const current = new Date();
      this.day = `${
        current.getMonth() + 1
      }/${current.getDate()}/${current.getFullYear()}`;
      const d = new Date(this.day);
      this.dayNumber = d.getDay();
      this.dayString = this.weekday[this.dayNumber];
      this.thisDay = current.getDate();
      this.month = this.monthNames[d.getMonth()];
      const fiveMinutesInMillis = 5 * 60 * 1000;
      d.setTime(d.getTime() + fiveMinutesInMillis);
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
  },

  beforeMount() {
    this.currentDate();
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.middle {
  text-align: center;
}

.middle p {
  position: relative;
  top: 25px;
}
.clock {
  font-size: 68px;
}
.bottom {
  position: relative;
  top: 350px;
  display: flex;
  justify-content: space-between;
  width: 85%;
  margin: auto;
}
.bottom button {
  background: #262626;
  border: none;
  width: 45px;
  height: 45px;
  border-radius: 25px;
}
</style>
<style>
.flashbang {
  box-shadow: 1px 10px 50px 40px yellow;
}

.maintwoBack {
  background-image: url("../assets/background.jpeg") !important;
}
</style>
