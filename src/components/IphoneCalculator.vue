<template>
    <div class="monitor">
      <input class="inpt" type="text" v-model="clickedNumber" readonly />
    </div>
    <div class="container place">
      <div class="row">
        <button
          v-for="(button, index) in buttons"
          :key="button.id"
          @click="pickNum(index), clValue(index)"
          class="butt"
          :class="{
            kenti: orrng(index),
            zero: zero(index),
            three: three(index),
          }"
        >
        {{ button }}
        </button>
      </div> 
    </div>
</template>

<script>
export default {
  data() {
    return {
      buttons: [
        "AC",
        "+/-",
        "%",
        "÷",
        "7",
        "8",
        "9",
        "x",
        "4",
        "5",
        "6",
        "-",
        "1",
        "2",
        "3",
        "+",
        "0",
        ".",
        "=",
      ],
      clickedNumber: "0",
      switcher: true,
      noIncludeNum: [0, 1, 2],
      saver: 0,
      savertwo: 0,
      symbol: "",
      answer: 0,
      equalless: true,
      core: 0,
      onOff: true,
      one: 0,
      two: 0,
      counter: 0,
    };
  },
  computed: {},
  methods: {
    orrng(id) {
      if (id % 4 == 3 || id == this.buttons.length - 1) {
        return true;
      } else {
        return false;
      }
    },
    zero(id) {
      if (this.buttons[id] == "0") {
        return true;
      } else {
        return false;
      }
    },
    three(id) {
      if (id < 3) {
        return true;
      } else {
        return false;
      }
    },
    pickNum(idx) {
      if (this.clickedNumber[0] == "0") {
        this.clickedNumber = "";
      }

      if (!this.savertwo) {
        if (
          this.buttons[idx] == "÷" ||
          this.buttons[idx] == "+" ||
          this.buttons[idx] == "-" ||
          this.buttons[idx] == "x"
        ) {
          if (!this.counter) {
            if (this.buttons[idx] == "÷" && !this.symbol) {
              this.symbol = "/";
            } else if (this.buttons[idx] == "x" && !this.symbol) {
              this.symbol = "*";
            } else if (!this.symbol) {
              this.symbol = this.buttons[idx];
            }
            this.saver = parseInt(this.clickedNumber);
            this.switcher = false;
          }
        }
      }
      if (
        idx > this.noIncludeNum.length &&
        idx != 7 &&
        idx != 11 &&
        idx != 15
      ) {
        if (this.buttons[idx] != "=") {
          this.clickedNumber += this.buttons[idx];
        }
        if (this.symbol && !this.switcher) {
          if (!this.counter) {
            this.clickedNumber == "";
            this.counter++;
          }
          // ------------------
          this.clickedNumber = this.buttons[idx];
          this.switcher = true;
        }

        if (this.saver && this.symbol) {
          this.savertwo = parseInt(this.clickedNumber);
          if (this.buttons[idx] == "=" && this.savertwo) {
            if (this.symbol == "÷") {
              this.symbol = "/";
            }
            if (this.symbol == "x") {
              this.symbol = "*";
            }
            console.log(
              "saver: " +
                this.saver +
                "  savertwo: " +
                this.savertwo +
                "  symbol: " +
                this.symbol
            );
            this.answer = eval("this.saver" + this.symbol + "this.savertwo");
            if (this.answer != "=") {
              console.log("answer" + this.answer);
              this.clickedNumber = this.answer;
            }
            this.saver = 0;
            this.savertwo = 0;
            this.counter = 0;
          }
        }
      }

      if (this.buttons[idx] && this.answer) {
        this.two++;
        if (this.two >= 2) {
          if (this.buttons[idx] != "=") {
            this.clickedNumber = this.buttons[idx];
          }
          this.switcher = true;
          this.saver = 0;
          this.savertwo = 0;
          this.symbol = "";
          this.answer = 0;
          this.equalless = true;
          this.core = 0;
          this.onOff = true;
          this.one = 0;
        }
      }

      if (this.saver && this.symbol) {
        this.one++;
        if (this.one > 2) {
          if (this.one == 2) {
            this.clickedNumber = this.buttons[idx];
          }
          this.savertwo = parseInt(this.clickedNumber);
        }
        if (this.buttons[idx] == "÷" && this.savertwo) {
          this.symbol = "/";
          this.saver = eval("this.saver" + this.symbol + "this.savertwo");
          this.clickedNumber = this.saver;
          this.symbol = this.buttons[idx];
          this.savertwo = "";
          this.switcher = !this.switcher;
          this.counter = 0;
        } else if (this.buttons[idx] == "x" && this.savertwo) {
          this.saver = eval("this.saver" + this.symbol + "this.savertwo");
          this.symbol = "*";
          this.clickedNumber = this.saver;
          this.symbol = this.buttons[idx];
          this.savertwo = "";
          this.switcher = !this.switcher;
          this.counter = 0;
        } else if (this.buttons[idx] == "-" && this.savertwo) {
          this.saver = eval("this.saver" + this.symbol + "this.savertwo");
          this.symbol = "-";
          this.clickedNumber = this.saver;
          this.symbol = this.buttons[idx];
          this.savertwo = "";
          this.switcher = !this.switcher;
          this.counter = 0;
        } else if (this.buttons[idx] == "+" && this.savertwo) {
          this.saver = eval("this.saver" + this.symbol + "this.savertwo");
          this.symbol = "+";
          this.clickedNumber = this.saver;
          this.symbol = this.buttons[idx];
          this.savertwo = "";
          this.switcher = !this.switcher;
          this.counter = 0;
        }
      }
      this.see();
    },

    clValue(id) {
      if (this.buttons[id] == "AC") {
        this.clearEveryThing();
      } else if (this.buttons[id] == "%") {
        this.saver = parseInt(this.clickedNumber);
        this.saver = this.saver / 100;
        this.clickedNumber = this.saver;
      } else if (this.buttons[id] == "+/-") {
        this.saver = parseInt(this.clickedNumber);
        this.saver = this.saver - this.saver * 2;
        this.clickedNumber = this.saver;
      }
    },

    clearEveryThing() {
      this.clickedNumber = "0";
      this.switcher = true;
      this.saver = 0;
      this.savertwo = 0;
      this.symbol = "";
      this.answer = 0;
      this.equalless = true;
      this.core = 0;
      this.onOff = true;
      this.one = 0;
      this.two = 0;
      this.counter = 0;
    },

    see() {
      console.log(
        "clickednumber: " + this.clickedNumber,
        "  switcher: " + this.switcher,
        "  saver: " + this.saver,
        "  savertwo: " + this.savertwo,
        "  symbol: " + this.symbol,
        "  answer: " + this.answer,
        "  equalless: " + this.equalless,
        "  core: " + this.core,
        "  onOff: " + this.onOff,
        "  one: " + this.one,
        "  two: " + this.two,
        "  counter: " + this.counter
      );
      if (
        this.clickedNumber.toString().length == 1 &&
        this.clickedNumber != "0" &&
        !this.savertwo
      ) {
        this.two = 0;
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.monitor {
  width: 100%;
  height: 190px;
  background-color: transparent;
  display: flex;
  align-items: flex-end;
  justify-content: space-around;
}

.place {
  height: 50%;
  text-align: center;
}
.row {
  justify-content: space-evenly;
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

.kenti {
  background-color: orange;
}
.kenti:active {
  background-color: #fbc78d;
}
.zero {
  width: 43% !important;
  border-radius: 30px;
  text-align: left;
  padding-left: 7.5% !important;
}

.inpt {
  color: white;
  background-color: transparent;
  border: none;
  width: 90%;
  align-items: center;
  height: 30%;
  font-size: xx-large;
  text-align: right;
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

.three {
  background-color: #a5a5a5;
  color: black !important;
}
</style>
