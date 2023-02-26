<template>
  <div class="heighter">
    <div class="nav">
      <div
        class="charcho"
        :class="{
          actived: missed,
        }"
      ></div>
      <button @click="allButton(), toggleAll()">All</button>
      <button @click="missButton(), toggleAllMissed()">Missed</button>
    </div>
    <div class="middle">
      <h1>Recents</h1>
      <div>
        <div
          v-show="showMissedCalls(user.id)"
          class="ujrebi"
          v-for="user in users"
          :key="user.id"
          
        >
          <div class="pirveli">
            <h6
              :class="{
                redded: missedCall(user.id),
              }"
            >
              {{ user.name }}
            </h6>
            <p>{{ user.platform }}</p>
          </div>
          <div class="meore">
            {{ user.time }}
            <img
              src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABkAAAAZCAYAAADE6YVjAAAACXBIWXMAAAsTAAALEwEAmpwYAAACJElEQVR4nMVWPW/UQBD18VWGOlCSf4CEKAIngXUzgQIUuL+QHppI9gxOz8eFv0EHgrQ0FFHw5Waca0Iogd9AKqO3SUjCxfY5OomRrJXHO/tmdt6+dRT9b8uy8gJr0SW1N6yWs/ovEtvHiPcDf9HFvHMBcDrqkfo2iY9IPeklo1uU5PM3V/LLGPHO4im+s9iQ0iKeevFu9vkSi78l8V1SfzRNzJIUj1n9G4kN+v13FxsBSPwDi3/kbHOuVeXZ5hypfUJ8LRAqAEDVpF42XiC15xjP+o44ALHaenUPxHfrKiC176xeYmuq5sSr+VUW25voEdgRmtzQAxbbawIJyYgtgwynWHdAU9+OGqyXjRdY/BmnOzfqZ5YdVrMHqd89iTwATaMZGokpq786dqh9Be/rgji1RZZiNTypLTaBcOK3SXzr2IGTnOTztZmlRUziX9ATUl9rAomz4TUW/3mytP1+Nr7SFEjqa9OCYD1S+92qkrYgD5PRdVL/0aonbUEmeyL+GmI3UxC1FyT+8q8DfIaazg6k7JCYk/qdU07cD1DTWYCw+FMkPXHPgKKQiyrtOgI4eqqAoF3QuKXU7p2dqdigToWbLKiw2AZuzNpJrPYeco2MohYWowKxDcQ3JnkItB7kWmy5efmy01N7gi1CBa12IfRIbAg1JXUB7yEVOMlBMsI5MAWLDn8y7k+9+L9Zgt5QUxwsaFH4WwmjbwV/oGnZOSfA7OwPW0iTUv3ECkQAAAAASUVORK5CYII="
            />
          </div>
        </div>
      </div>
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
      users: [
        {
          id: 1,
          name: "John Doe",
          platform: "Messenger Audio ",
          time: "18:17",
        },
        { id: 2, name: "Jane Smith", platform: "Mobile", time: "04:58" },
        {
          id: 3,
          name: "Bob Johnson",
          platform: "WhatsApp Audio",
          time: "03:22",
        },
        { id: 4, name: "Johny Walker", platform: "Viber Video", time: "02:54" },
        { id: 5, name: "Sam Lee", platform: "Telegram Call", time: "02:50" },
        {
          id: 6,
          name: "Adam Black",
          platform: "Messenger Video",
          time: "01:33",
        },
        {
          id: 7,
          name: "George Wrangler",
          platform: "Phone Call",
          time: "01:33",
        },
        { id: 8, name: "Gaby Charlie", platform: "FaceTime", time: "01:33" },
        {
          id: 9,
          name: "Jack Davies",
          platform: "WahatsApp Video",
          time: "01:33",
        },
        { id: 10, name: "Oliver Thompson", platform: "Mobile", time: "01:33" },
        { id: 11, name: "Jacob Hall", platform: "Mobile", time: "01:33" },
        { id: 12, name: "Charlie Jackson", platform: "Mobile", time: "01:33" },
      ],
      all: false,
      missed: false,
    };
  },

  methods: {
    toggleAllMissed() {
      this.all = true;
    },
    toggleAll() {
      this.all = false;
    },
    showMissedCalls(id) {
      if (!this.all) {
        return true;
      } else if (this.all) {
        if (id % 3 == 2 || id == 3) {
          return true;
        }
      }else{
        return false;
      }
    },
    missedCall(id) {
      if (id % 3 == 2 || id == 3) {
        return true;
      } else {
        return false;
      }
    },
    allButton() {
      this.missed = false;
    },
    missButton() {
      this.missed = true;
    },
  },
};
</script>

<style scoped>

.redded {
  color: red !important;
}
.charcho {
  height: 32px;
  width: 70px;
  position: absolute;
  background: #5a5a5f;
  border-radius: 5px;
  transition: transform 0.2s ease;
}
.actived {
  transform: translateX(70px);
}
.slideup {
  transform: translateY(70px);
}
.heighter {
  height: 501px;
}
.nav {
  background-color: #1c1c1f;
  width: 49%;
  position: relative;
  left: 27%;
  padding: 2px;
  border-radius: 6px;
}
.nav button {
  background-color: transparent;
  border: none;
  width: 70px;
  height: 32px;
  border-radius: 6px;
  transition: background-color 0.5s ease;
  z-index: 1;
}

.middle {
  height: 105%;
  padding-left: 10%;
  overflow: scroll;
  -ms-overflow-style: none; /* IE and Edge */
  scrollbar-width: none; /* Firefox */
  max-height: 96%;
  overflow: auto;
  border-bottom-right-radius: 1em;
}
.middle::-webkit-scrollbar {
  display: none; /* Chrome, Safari and Opera */
}
.ujrebi {
  height: 50px;
  border-top: #5a5a5f solid;
  display: flex;
  justify-content: space-between;
  color: white;
}
.ujrebi h6 {
  margin-bottom: 1px;
  font-size: medium;
  font-family: system-ui;
}
.ujrebi p {
  font-size: smaller;
  color: #8d8d92;
  font-size: 0.7em;
}
.pirveli {
  width: 130px;
  height: 100%;
}
.meore {
  width: 70px;
  height: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  align-items: center;
  color: #8d8d92;
  font-size: 0.8em;
}
</style>

