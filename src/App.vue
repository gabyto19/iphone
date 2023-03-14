<template>
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link
      href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css"
      rel="stylesheet"
      integrity="sha384-GLhlTQ8iRABdZLl6O3oVMWSktQOp6b7In1Zl3/Jr59b6EGGoI1aFkw7cmDA6j6gD"
      crossorigin="anonymous"
    />
    <link rel="stylesheet" href="style.css" />
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
      href="https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,500;1,300&display=swap"
      rel="stylesheet"
    />
  </head>
  <body>
    <div
      class="maintwo"
      :class="{ maintwoBack: wallpaper, flashbang: makeLight }"
      @dblclick="unlockScreen"
    >
      <nav>
        <p class="network">NETWORK</p>
        <div class="cholka"></div>
        <div class="nav-icons">
          <img
            src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABEAAAARCAYAAAA7bUf6AAAACXBIWXMAAAsTAAALEwEAmpwYAAAAe0lEQVR4nOXUsQmAMBCF4VTiAILoBtYWVuIAVqbOWGLhMFnDcX4RUlyCIF4REA8eBJJ8xZGcMS8LKAAr0hoFUgEecMB2QVpkD2uXDwFqYBUZNEhHXMuHEKAHDpFZg4zJJZsHAcrr6YpMGuTu0M8QH/3i0Ew5H5p0Xjztn9RPkOfpuq1uAAAAAElFTkSuQmCC"
          />
          <img
            src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABkAAAAZCAYAAADE6YVjAAAACXBIWXMAAAsTAAALEwEAmpwYAAAB90lEQVR4nO3VS0gVcRQG8KsiGmakbkJICjeVrQNb3lyJ1SIqqEVQyFUKXfUgglpW1KK3UC4iEIoi6AFBi+i1ElvULnLRgx5QkG5q94t/nIFhQE257TwwDOf8v/N9M989Z26ptBjVDDRhI/bgEA7jYOSp3rRQ4lYcwDP8wjhu4BRO4nTk43H+FPvR8i/kLTiDKdzGLrTN0dOG3biDn/EAy2cCb8dX3MS6wtlabMVA2DUQ+ZoCrgu38AXb8gd1uIhv2JSrd+IcJvEO9zASdo1EPhlXwnXmenuC73ziT4UxvEJ7AFZgFJ9xLD3dHHZ1BS7hr6X+qLcH71hedQPKeI/jaC4MQh8qYVcl8tYcphknor8cfIm3JwOkhh/4gO5c4xY8iUF4hMth15XIp+J8c66nGx+Dr6/42r05y1bjBV5jBxpnsKoRO/EGz7EqZ1XvbB6XY8qOojY3HN0YDLsGI6+L89rAp77ybL9hJtIfr9sR5EP4hImwKZuuiagPBa4j+vrnFAmhYbwNC+4X9yaLVMeDwCX8cGk+gSNx1US+EvvCrr0pj3pNhp2XQEGsARcwjbs4G/fpWLaGBZPnRNJO/C4uJdZHvVINkWTHJbzE0qgtif0YzeysltBVPMYyPMT1bMSrFjGm6Qv9Pe5/d6Tqgfr4d6z/LwKLkeIP10YjABOEb3UAAAAASUVORK5CYII="
          />
          <img
            src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABkAAAAZCAYAAADE6YVjAAAACXBIWXMAAAsTAAALEwEAmpwYAAAArUlEQVR4nO3SMQ4BQRiG4S304gbOQEi0Sg4gElHq3ELCFeg1Cq1Go1AoNTqcQClRSB7NbrORlcV0+yZfN9+88/+ZKCooCA5KGGCK2ReZoPNJsvAfxlmSW+rwGvMc2cS9XZbknpI0cq67G/euGKEfUpJwCSGpYYVtMEkCmiEnKaOOYUhJN9UPKnng/PYrv5G0UcmRXtw7ZL3k6D8ssyQtnH64/Ik9qnnWXFAQ/cQLpLKjtMRh0WkAAAAASUVORK5CYII="
          />
        </div>
      </nav>
      <div class="ekrani">
        <IphoneCalculator v-if="calculatorComp"></IphoneCalculator>
        <lockScreen
          @toggle-camera="chartva"
          v-if="butLockScreen"
          @flashLight="bright"
        ></lockScreen>
        <menuPage
          @toggle-msg="toggleMessage"
          @toggle-variable="handleToggleVariable"
          @toggle-calc="toggleCalculator"
          @toggle-camera="chartva"
          @toggle-facetime="toggleFacetime"
          @toggle-clock="toggleClock"
          v-if="menuComp"
        ></menuPage>
        <callPage v-if="callComp"></callPage>
        <messagePage v-if="messageComp"></messagePage>
        <facetimePage v-if="facetimeComp"></facetimePage>
        <clockPage v-if="clockComp"></clockPage>
      </div>
    </div>
    <footer>
      <p>Beta Version</p>
      <br />
      <p>Working functions:</p>
      <ol>
        <li>FlashLight</li>
        <br />
        <li>Camera</li>
        <br />
        <li>Time(Clock)</li>
        <br />
        <li>Weather</li>
        <br />
        <li>FaceTime</li>
        <br />
        <li>Calculator</li>
        <br />
        <li>Call</li>
        <br />
        <li>Messages</li>
        <br />
        <li>Safari</li>
      </ol>
    </footer>
  </body>
</template>

<script>
import IphoneCalculator from "./components/IphoneCalculator.vue";
import lockScreen from "./components/lockScreen.vue";
import menuPage from "./components/menuPage.vue";
import callPage from "./components/callPage.vue";
import messagePage from "./components/childComponents/menuComponents/messagePage.vue";
import facetimePage from "./components/childComponents/menuComponents/facetimePage.vue";
import clockPage from "./components/childComponents/menuComponents/clockPage.vue";
export default {
  name: "App",
  components: {
    IphoneCalculator,
    lockScreen,
    menuPage,
    callPage,
    messagePage,
    facetimePage,
    clockPage,
  },
  data() {
    return {
      butLockScreen: true,
      makeLight: false,
      wallpaper: true,
      calculatorComp: false,
      menuComp: false,
      callComp: false,
      messageComp: false,
      facetimeComp: false,
      clockComp: false,
    };
  },
  methods: {
    chartva() {
      this.wallpaper = false;
    },
    toggleClock() {
      this.butLockScreen = false;
      this.makeLight = false;
      this.wallpaper = false;
      this.calculatorComp = false;
      this.menuComp = false;
      this.callComp = false;
      this.messageComp = false;
      this.facetimeComp = false;
      this.clockComp = true;
    },
    toggleMessage() {
      this.butLockScreen = false;
      this.makeLight = false;
      this.wallpaper = false;
      this.calculatorComp = false;
      this.menuComp = false;
      this.callComp = false;
      this.messageComp = true;
      this.facetimeComp = false;
      this.clockComp = false;
    },
    toggleCalculator() {
      this.butLockScreen = false;
      this.makeLight = false;
      this.wallpaper = false;
      this.calculatorComp = true;
      this.menuComp = false;
      this.callComp = false;
      this.messageComp = false;
      this.facetimeComp = false;
      this.clockComp = false;
    },
    handleToggleVariable() {
      this.butLockScreen = false;
      this.makeLight = false;
      this.wallpaper = false;
      this.calculatorComp = false;
      this.menuComp = false;
      this.callComp = true;
      this.messageComp = false;
      this.facetimeComp = false;
      this.clockComp = false;
    },
    toggleFacetime() {
      this.butLockScreen = false;
      this.makeLight = false;
      this.wallpaper = false;
      this.calculatorComp = false;
      this.menuComp = false;
      this.callComp = false;
      this.messageComp = false;
      this.facetimeComp = true;
      this.clockComp = false;
    },

    unlockScreen() {
      if (this.butLockScreen) {
        this.butLockScreen = false;
        this.menuComp = true;
      }
    },
    bright() {
      this.makeLight = !this.makeLight;
    },
  },
};
</script>

<style>
* {
  font-family: "Roboto", sans-serif;
  color: white;
}

body {
  background-color: blanchedalmond !important;
}

nav {
  display: flex;
  width: 90%;
  margin: auto;
  justify-content: space-between;
}
.nav-icons {
  width: 68px;
  display: flex;
  align-items: center;
  justify-content: space-around;
}
.nav-icons img {
  width: 17px;
}
.network {
  position: relative;
  top: 10px;
  font-family: sans-serif;
  font-size: smaller;
  width: 68px;
}

.maintwo {
  margin: auto;
  height: 600px;
  width: 310px;
  position: relative;
  top: 2%;
  border-radius: 1.5em;
  background-size: cover;
  background-color: black;
  border: #262626;
  border-style: solid;
  border-width: 7px;
  position: relative;
  top: 100px;
  margin: auto;
  z-index: 0;
}
.cholka {
  width: 40%;
  background-color: #262626;
  height: 30px;
  border-bottom-left-radius: 1em;
  border-bottom-right-radius: 1em;
  align-items: center !important;
  z-index: 50;
}

footer {
  position: relative;
  top: 100px;
  width: 100%;
}

footer p,
li {
  color: black !important;
}
footer li {
  width: 100px;
  margin-left: 30px;
}

footer ol {
  display: flex;
}
</style>
