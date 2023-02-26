<template>
  <div class="heighter">
    <div class="top">
      <p>
        <img style="height: 16px" src="../../../assets/Call/Arrow.png" alt="" />
        Lists
      </p>
      <button>
        <img style="height: 16px" src="../../../assets/Call/plus.png" alt="" />
      </button>
    </div>
    <div class="middle">
      <h1>Contacts</h1>
      <div class="dzebna">
        <img
          src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAAAUCAYAAACNiR0NAAAACXBIWXMAAAsTAAALEwEAmpwYAAABmUlEQVR4nL1UPUscURQdP4oYLO20C8EqQVCrqIsg+AumWIdz3rt3l0G2Mpi0jq1gJ/4C0dhpgukVAmnFQuwNEQQTTPwiUZS3+7aR3ZnRFU81wz1z7rlfEwTPAWvta0DmAdkC5DspG4DMFItxz4OECoWkk9RFUv6TekvKT0D3ADmpvespact59dpIXfdCX8jS23ogSZJ2QCZI3XVxQD9mqgE6XSPLkhNvxInj+CWp24DcADrUVCypOtAfpOy7stMSk+wF5ByQz01J1tph724ms5SqqKwCemmMedGQAJSmfNPH8ggCMuv4bhuCJhmL3mEhn0P94PhRpP2pJZPyPp9DXQPkKgzDrqZDIeWQlIOsoURRuY/UC1I3U7MaI7F3uZy2NoDskHptTHkwq5I2Uj754Xw1xgzUA2EYdgB20l2N77Vbm5EswaD2oS4A8s9fxFHt9PS3d/+L1DP//DeK7GiQByRfATLnfw7fAF0BtBKGlW63Wo8STYMxpXeA/KmXT+p40CruO2XOo8jlFNBja+2blgUdXA+fTKwR7gDVftvnMOpI9gAAAABJRU5ErkJggg=="
        />
        <input class="search" type="text" placeholder="Search" />
      </div>
      <div class="userclass">
        <img src="../../../assets/Call/user.png" alt="" />
        <p>My Card</p>
      </div>
      <ul>
        <li v-for="user in sortedUsers" :key="user.id">
          {{ user.name }}
        </li>
      </ul>
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
    };
  },
  computed: {
    sortedUsers() {
      return [...this.users].sort((a, b) => a.name.localeCompare(b.name));
    },
  },

  methods: {},
};
</script>

<style scoped>

.middle li{
    border-top: solid grey 1px;
    list-style: none;
    height: 40px;
    padding-top: 5px;
    font-size: 12px;
}
.middle ul{
    padding: 0;
    
}
.userclass {
  height: 70px;
  margin-top: 10px;
  margin-bottom: 10px;
  border-top: solid #5e5e62 1px;
  display: flex;
  align-items: center;
}
.userclass img {
  width: 50px;
  height: 50px;
  margin-top: 10px;
}
.userclass p {
  margin: 0;
  margin-left: 13px;
  margin-top: 5px;
  font-size: 12px;
  color: #5e5e62;
}
.dzebna img {
  width: 20px;
  height: 20px;
  margin-top: 5px;
  margin-left: 5px;
}
.dzebna input {
  outline: none;
  color: white;
  height: 30px;
}
.dzebna {
  display: flex;
  background: #1c1c1e;
  border-radius: 6px;
  width: 95%;
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
}
.search {
  width: 80%;
  background: #1c1c1e;
  border: none;
  border-radius: 6px;
  color: #5e5e62;
}
.heighter {
  height: 501px;
}
.top {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 95%;
  margin: auto;
}
.top p {
  margin: 0;
  color: #1f8bff;
}
.top div {
  width: 30px;
  height: 5px;
}
.top button {
  border: none;
  background: none;
  color: #1f8bff;
}
.middle {
  height: 105%;
  padding-left: 5%;
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
</style>
