<template>
  <div v-if="browser">
    <div class="upperSide">
      <div class="weather">
        <div class="wePosition" :class="{ loading: this.button }">
          <div>
            <p style="margin: 0px 0px 0px 6px; height: 18px">{{ city }}</p>
            <h2 :class="{ loading: this.button }">{{ temperature }}</h2>
          </div>
          <div class="dabla">
            <p style="padding: 0 0 0 6px; margin: 0px">{{ bu }}</p>
            <p>{{ high }} {{ low }}</p>
          </div>
        </div>
      </div>
      <div class="battery">
        <div class="grid-item">
          <img
            class="phone-icon-class"
            src="../assets/phone-icon.png"
            alt="Phone"
          />
          <svg style="top: 4px">
            <circle cx="27" cy="25" r="25" />
            <circle cx="-30" cy="32" r="25" style="stroke-dashoffset: 50px" />
          </svg>
        </div>
        <div class="grid-item">
          <img
            class="watch-icon-class"
            src="../assets/watch-icon.png"
            alt="watch"
          />
          <svg style="top: 4px">
            <circle cx="27" cy="25" r="25" />
            <circle cx="-30" cy="32" r="25" style="stroke-dashoffset: 10px" />
          </svg>
        </div>
        <div class="grid-item">
          <img
            class="airpods-icon-class"
            src="../assets/airpods-icon.png"
            alt="airpods"
          />
          <svg>
            <circle cx="27" cy="25" r="25" />
            <circle cx="-30" cy="32" r="25" style="stroke-dashoffset: 100px" />
          </svg>
        </div>
        <div class="grid-item">
          <img
            class="airpodsCase-icon-class"
            src="../assets/airpodCase-icon.png"
            alt="airpodscase"
          />
          <svg>
            <circle cx="27" cy="25" r="25" />
            <circle
              cx="-30"
              cy="32"
              r="25"
              style="stroke-dashoffset: 125px; stroke: red"
            />
          </svg>
        </div>
      </div>
    </div>
    <div class="middleSide">
      <div
        v-for="(button, index) in icons"
        :key="button.id"
        @click="toggleCalculator(button)"
      >
        <button
          :class="{
            faceTimeClass: faceTime(index),
            calendar: calendar(index),
            mailClass: mail(index),
            notesClass: notes(index),
            photosClass: photos(index),
            tvClass: tv(index),
            podcastClass: podcast(index),
            remindersClass: reminders(index),
            clockClass: clock(index),
            healthClass: health(index),
            calculatorClass: calculator(index),
            walletClass: wallet(index),
            appStoreClass: appStore(index),
            mapsClass: maps(index),
            settingsClass: settings(index),
            googleMapsClass: googleMaps(index),
          }"
          class="homeIcons"
        ></button>
        <label>{{ button }}</label>
      </div>
    </div>
    <div class="bottom-side">
      <button @click="toggleVariable" class="callClass homeIcons"></button>
      <button @click="toggleMessage" class="messagesClass homeIcons"></button>
      <button @click="openBrowser()" class="safariClass homeIcons"></button>
      <button @click="startCamera(),openCamera()" class="cameraClass homeIcons"></button>
    </div>
    <video ref="videoElement" autoplay></video>
  </div>

  <div class="saiti" v-else-if="browserOn">
    <iframe
      src="https://www.google.com/"
      frameborder="0"
      allowfullscreen=""
      webkitallowfullscreen="true"
      mozallowfullscreen="true"
      oallowfullscreen="true"
      msallowfullscreen="true"
    ></iframe>
  </div>
  <div>
    <video
      style="height: 50px; margin-top: 40%; height: 100%; width: 100%"
      ref="videoElement"
      autoplay
    ></video>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      icons: [
        "FaceTime",
        "Calendar",
        "Mail",
        "Notes",
        "Photos",
        "TV",
        "Podcasts",
        "Reminders",
        "Clock",
        "Health",
        "Calculator",
        "Wallet",
        "App Store",
        "Maps",
        "Settings",
        "Google Maps",
      ],
      city: "Loading...",
      temperature: "Loading...",
      button: true,
      bu: "Loading...  ",
      high: "Loading...  ",
      low: "Loading...  ",
      browser: true,
      browserOn: false,
      camera: false,
    };
  },

  created() {
    this.qalaqi();
  },

  watch: {
    city: function (newValue, oldValue) {
      if (newValue != oldValue) {
        this.getWeather();
      }
    },
  },

  methods: {
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
    openCamera(){
      this.$emit('toggle-camera');
    },
    openBrowser() {
      this.browser = false;
      this.browserOn = true;
    },

    toggleMessage() {
      this.$emit("toggle-msg");
    },
    toggleCalculator(button) {
      if (button == "Calculator") {
        this.$emit("toggle-calc");
      }
      if (button == "FaceTime")
      {
        this.$emit("toggle-facetime");
      }
      if(button == "Clock"){
        this.$emit("toggle-clock");
      }
    },
    toggleVariable() {
      this.$emit("toggle-variable");
    },
    async getWeather() {
      const API_KEY = "b5a6f2e6379ec2b7e1e5eeabe4e3383b";
      const weather = await axios.get(
        `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=${API_KEY}`
      );
      this.temperature = Math.round(weather.data.main.temp - 273.15) + "°";
      this.bu = weather.data.weather[0].main;
      this.high =
        "H:" + eval(Math.round(weather.data.main.temp - 273.15) + 5) + "°";
      this.low =
        "L:" + eval(Math.round(weather.data.main.temp - 273.15) - 5) + "°";
      this.button = false;
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

    faceTime(id) {
      if (id == 0) {
        return true;
      }
    },
    calendar(id) {
      if (id == 1) {
        return true;
      }
    },
    mail(id) {
      if (id == 2) {
        return true;
      }
    },
    notes(id) {
      if (id == 3) {
        return true;
      }
    },
    photos(id) {
      if (id == 4) {
        return true;
      }
    },
    tv(id) {
      if (id == 5) {
        return true;
      }
    },
    podcast(id) {
      if (id == 6) {
        return true;
      }
    },
    reminders(id) {
      if (id == 7) {
        return true;
      }
    },
    clock(id) {
      if (id == 8) {
        return true;
      }
    },
    health(id) {
      if (id == 9) {
        return true;
      }
    },
    calculator(id) {
      if (id == 10) {
        return true;
      }
    },
    wallet(id) {
      if (id == 11) {
        return true;
      }
    },
    appStore(id) {
      if (id == 12) {
        return true;
      }
    },
    maps(id) {
      if (id == 13) {
        return true;
      }
    },
    settings(id) {
      if (id == 14) {
        return true;
      }
    },
    googleMaps(id) {
      if (id == 15) {
        return true;
      }
    },
  },
};
</script>

<style scoped>
.saiti {
  position: relative;
  width: 100%;
  height: 587px;
  top: -36px;
}
.saiti iframe {
  width: 100%;
  height: 100%;
  border-radius: 16px;
}
.callClass {
  background-image: url("../assets/call.png");
  background-size: cover;
}

.messagesClass {
  background-image: url("../assets/messages.png");
  background-size: cover;
}

.safariClass {
  background-image: url("../assets/safari.png");
  background-size: cover;
}
.cameraClass {
  background-image: url("../assets/camera.png ");
  background-size: cover;
}
.bottom-side {
  width: 94%;
  position: relative;
  top: 23px;
  height: 71px;
  border-radius: 1em;
  background-color: #222222c4;
  margin: auto;
  display: flex;
  justify-content: space-around;
  align-items: center;
}

.airpodsCase-icon-class {
  position: absolute;
  width: 35px;
  margin-top: 17px;
  margin-left: 15px;
}
.airpods-icon-class {
  position: absolute;
  width: 64px;
  margin-top: 4px;
}

.watch-icon-class {
  position: absolute;
  margin-left: 21px;
  margin-top: 20px;
  width: 20px;
}

.phone-icon-class {
  position: absolute;
  margin-left: 23px;
  width: 16px;
  margin-top: 21px;
}

svg {
  position: relative;
  width: 63px;
  height: 63px;
}
svg circle {
  fill: none;
  stroke: rgba(255, 255, 255, 0.05);
  stroke-width: 4;
  transform: translate(5px, 5px);
  stroke-linecap: round;
}
svg circle:nth-child(2) {
  stroke: #45e945;
  stroke-dasharray: 150px;
  transform: rotate(-90deg);
}

.dabla p {
  font-family: inherit;
  margin-left: 6px;
  font-size: small;
}
.calendar {
  background-image: url("../assets/calendar.png") !important;
  background-color: transparent !important;
  background-size: cover;
}

.notesClass {
  background-image: url("../assets/notes.png") !important;
  background-color: transparent !important;
  background-size: cover;
}
.faceTimeClass {
  background-image: url("../assets/facetime.png") !important;
  background-color: transparent !important;
  background-size: cover;
}
.mailClass {
  background-image: url("../assets/mail.png") !important;
  background-color: transparent !important;
  background-size: cover;
}

.photosClass {
  background-image: url("../assets/photos.png") !important;
  background-color: transparent !important;
  background-size: cover;
}

.tvClass {
  background-image: url("../assets/tv.png") !important;
  background-color: transparent !important;
  background-size: cover;
}

.podcastClass {
  background-image: url("../assets/podcasts.png") !important;
  background-color: transparent !important;
  background-size: cover;
}
.remindersClass {
  background-image: url("../assets/reminders.png") !important;
  background-color: transparent !important;
  background-size: cover;
}

.clockClass {
  background-image: url("../assets/clock.png") !important;
  background-color: transparent !important;
  background-size: cover;
}
.healthClass {
  background-image: url("../assets/health.png") !important;
  background-color: transparent !important;
  background-size: cover;
}
.calculatorClass {
  background-image: url("../assets/calculator.png") !important;
  background-color: transparent !important;
  background-size: cover;
}

.walletClass {
  background-image: url("../assets/wallet.png") !important;
  background-color: transparent !important;
  background-size: cover;
}

.appStoreClass {
  background-image: url("../assets/appStore.png") !important;
  background-color: transparent !important;
  background-size: cover;
}

.mapsClass {
  background-image: url("../assets/maps.png") !important;
  background-color: transparent !important;
  background-size: cover;
}
.settingsClass {
  background-image: url("../assets/settings.png") !important;
  background-color: transparent !important;
  background-size: cover;
}

.googleMapsClass {
  background-image: url("../assets/googleMaps.png") !important;
  background-color: transparent !important;
  background-size: cover;
}

.weather {
  height: 130px;
  width: 130px;
  background-color: blue;
  background: linear-gradient(to bottom, #054784, #74a0cb);
  border-radius: 20px;
}

.battery {
  height: 130px;
  width: 130px;
  background-color: #30281f;
  border-radius: 20px;
  opacity: 0.9;
  display: grid;
  grid-template-columns: auto auto;
}

.upperSide {
  display: flex;
  justify-content: space-around;
  position: relative;
  top: 20px;
}

.homeIcons {
  width: 50px;
  height: 50px;
  border-radius: 15px;
  background-color: black;
  border: none;
}
.middleSide {
  grid-template-columns: 55px 55px 55px 55px;
  display: grid;
  gap: 0px 18px;
  position: relative;
  top: 33px;
  left: 12px;
  text-align: center;
}
.middleSide label {
  font-size: x-small;
  position: relative;
  top: -8px;
}

.middleSide label {
  font-family: inherit;
}
.wePosition {
  height: inherit;
  margin: 10px;
}
.wePosition h2 {
  font-family: sans-serif;
  margin-left: 10px;
}

.loading {
  font-size: xx-small !important;
}
</style>

<style>
.maintwo {
  background-color: black !important;
}
</style>
