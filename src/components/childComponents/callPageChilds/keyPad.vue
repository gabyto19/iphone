<template>
  <div class="display">
    <div class="monitor">
      <input class="inpt" type="text" v-model="clickedNumber" readonly />
    </div>
  </div>

  <div class="keyboard">
    <button
      class="butt"
      v-for="(button, index) in buttons"
      :key="button.id"
      @click="pickNum(index)"
    >
      {{ button }}
    </button>
  </div>
  <button class="call-butt">
    <img
      src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAACXBIWXMAAAsTAAALEwEAmpwYAAABKklEQVR4nO3VPSuFUQDA8ecWixgsXorRjoRZ4iofQCmjL+AOlNFoMhkobEqUMpoMJkoZlIxSwiRc0k+3Hrk9PfdFPeeW8l/P8DvndF6i6L9E6MMytjAYhQ4d2MGnn27RFBIdwp30pkPCxyp3EBK+qgK/ozMUfK56hVDwfg34NBS8VANeDwX3V0Ev0B4KzuEyBb1GVxD0O8w3bIvLQwseE/AreqPQYSVl1buNgNvi9znZWCPwuRT4pjSp0HAOJyn4ZlC4FAZQTMFn4/FmTGERI1GWoZACv2EbD4mTn896y4/UVzHTfxvduK8TL618Mkt8FM+/wMezxPMVDltaZ5nBMT6DjzrgjUzhGJ/AUxV0D62ZwzHeg8ME+IKF0k0IgpaHYaxhtSE/WPTX+gLbt1xuiUFY5QAAAABJRU5ErkJggg=="
    />
  </button>
  <button class="delete" @click="deleter()">x</button>
  
</template>

<script>
export default {
  data() {
    return {
      buttons: ["1", "2", "3", "4", "5", "6", "7", "8", "9", "*", "0", "#"],
      clickedNumber: "",
    };
  },

  methods: {
    pickNum(index) {
      this.clickedNumber += this.buttons[index];
    },
    deleter() {
      if (this.clickedNumber) {
        const words = this.clickedNumber.split("");
        words.pop();
        let newString = words.join("");
        this.clickedNumber = newString;
      }
    },
  },
};
</script>

<style scoped>
.delete {
  clip-path: polygon(25% 20%, 100% 20%, 100% 80%, 25% 80%, 0% 50%);
  border-radius: 4px;
  width: 31px;
  height: 26px;
  position: relative;
  left: 55%;
  top: 17px;
  background-color: #343434;
  color: white;
  padding-bottom: 27px;
}

.call-butt {
  width: 60px;
  height: 59px;
  border-radius: 50%;
  border: none;
  background-color: #67ce67;
  position: relative;
  left: 40%;
  top: 12px;
  margin-bottom: 25px;
}
.display {
  width: 85%;
  height: 140px;
  margin: auto;
}
.keyboard {
  display: grid;
  grid-template-columns: auto auto auto;
  justify-items: center;
  justify-content: space-evenly;
  row-gap: 3px;
}
.monitor {
  width: 100%;
  height: 190px;
  background-color: transparent;
  display: flex;
  align-items: flex-end;
  justify-content: space-around;
}
.inpt {
  color: white;
  background-color: transparent;
  border: none;
  width: 90%;
  align-items: center;
  height: 100%;
  font-size: xx-large;
  text-align: center;
}
.inpt:focus {
  outline: none;
}
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

/* Firefox */
input[type="number"] {
  -moz-appearance: textfield;
}

.butt {
  border-radius: 50%;
  height: 60px;
  width: 60px !important;
  border-style: solid;
  margin: 7px 1.5px 0 1.5px !important;
  background-color: #343434;
  color: white !important;
  border: none;
  font-size: x-large;
}

.butt:active {
  background-color: #737373;
}

</style>
