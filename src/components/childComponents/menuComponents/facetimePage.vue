<template>
  <div class="bodyClass">
    <p style="color: #5db05c; margin-bottom: 10px">Edit</p>
    <h5 style="margin-bottom: 15px">FaceTime</h5>
    <div class="heade">
      <div class="link">
        <img src="../../../assets/Facetime/chain.png" alt="" />
        <p>Create Link</p>
      </div>
      <div class="newface">
        <img src="../../../assets/Facetime/camera.png" alt="" />
        <p>new FaceTime</p>
      </div>
    </div>
    <p style="color: gray; font-size: 11px; margin-left: 25px">LAST YEAR</p>
    <div class="callList">
      <div class="ujra" v-for="user in users" :key="user.id">
        <img src="../../../assets/Call/user.png" alt="" />
        <div class="conten">
          <div>
            <h6>{{ user.name }}</h6>
            <p>{{ user.platform }}</p>
          </div>
          <div>
            <p>{{ user.time }}</p>
            <img src="../../../assets/Facetime/Info.png" alt="" />
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
      users: [
        {
          id: 1,
          name: "(861) 547-4781",
          platform: "FaceTime Video ",
          time: "17.12.22",
        },
        {
          id: 2,
          name: "(634) 533-4623",
          platform: "FaceTime Video ",
          time: "13.12.22",
        },
        {
          id: 3,
          name: "(200) 895-0096",
          platform: "FaceTime Video ",

          time: "11.12.22",
        },
        {
          id: 4,
          name: "(490) 402-0007",
          platform: "FaceTime Video ",
          time: "08.12.22",
        },
        {
          id: 5,
          name: "(661) 511-4165",
          platform: "FaceTime Video ",
          time: "04.12.22",
        },
        {
          id: 6,
          name: "(398) 855-8283",
          platform: "FaceTime Video ",
          time: "19.11.22",
        },
        {
          id: 7,
          name: "(476) 333-2015",
          platform: "FaceTime Video ",
          time: "03.11.22",
        },
      ],
    };
  },

  methods: {},
};
</script>

<style scoped>
video {
  transform: rotate(-90deg);
  position: relative;
  left: -49px;
  top: -362px;
  height: 295.8px;
  z-index: 0;
}
.conten {
  display: flex;
  justify-content: space-between;
}
.conten div:first-child {
  width: 140px;
  margin-top: 3%;
  margin-left: 4%;
}
.conten div:nth-child(2) {
  width: 83px;
  display: flex;
  align-items: center;
  justify-content: space-evenly;
}
.conten h6 {
  font-size: 14px;
  margin: 0;
}
.conten p {
  font-size: 11px;
  color: gray;
  margin: 0;
}
.callList div:first-child {
  border: none;
}
.ujra {
  height: 43px;
  width: 95%;
  border-top: solid gray 1px;
  margin-left: 5%;
  display: flex;
}
.ujra img:first-child {
  height: 30px;
  margin-top: 6px;
}
.ujra img:nth-child(2) {
  height: 20px;
}
.callList {
  background-color: #52524c;
  height: 301px;
  border-radius: 10px;
}
.bodyClass {
  margin: 5%;
  z-index: 5;
}
.heade {
  display: flex;
  justify-content: space-between;
}
.heade div {
  width: 48%;
  height: 58px;
  border-radius: 10px;
}
.link {
  background-color: #52524c;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-end;
  margin-bottom: 15px;
}
.link img {
  height: 20px;
}
.link p {
  margin-bottom: 5px;
  font-size: 13px;
}
.newface {
  background-color: #43d945;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-end;
}
.newface img {
  height: 18px;
}
.newface p {
  margin-bottom: 5px;
  font-size: 13px;
}
</style>
