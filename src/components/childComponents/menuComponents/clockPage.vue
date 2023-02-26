<template>
  <worldPage v-if="false"></worldPage>
  <alarmPage v-if="false"></alarmPage>
  <stopwatchPage></stopwatchPage>

  <div class="bottom-nav">
    <div>
      <button style="position: relative; left: 8px">
        <img src="../../../assets/Clock/world.png" alt="" />
      </button>
      <p>World Clock</p>
    </div>
    <div>
      <button>
        <img src="../../../assets/Clock/alarm.png" alt="" />
      </button>
      <p>Alarm</p>
    </div>
    <div>
      <button>
        <img src="../../../assets/Clock/stopwatch.png" alt="" />
      </button>
      <p>Stopwatch</p>
    </div>
    <div>
      <button>
        <img src="../../../assets/Clock/timer.png" alt="" />
      </button>
      <p>Timer</p>
    </div>
  </div>
</template>

<script>
import worldPage from "../clockComponents/worldPage.vue";
import alarmPage from "../clockComponents/alarmPage.vue";
import stopwatchPage from "../clockComponents/stopwatchPage.vue";

export default {
  components: {
    worldPage,
    alarmPage,
    stopwatchPage,
  },
  data() {
    return {};
  },

  methods: {},
};
</script>

<style scoped>
.bottom-nav {
  width: 100%;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  position: relative;
}
.bottom-nav button {
  background: none;
}
.bottom-nav img {
  height: 25px;
}
.bottom-nav p {
  font-size: 10px;
  text-align: center;
}
</style>
