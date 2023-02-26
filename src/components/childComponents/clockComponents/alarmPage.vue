<template>
  <div class="mtavari">
    <div class="tavi">
      <button>Edit</button>
      <p>Alarm</p>
      <img src="../../../assets/Clock/plus.png" alt="" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  methods: {},
};
</script>

<style scoped>
.mtavari {
  height: 480px;
}
.tavi {
  display: flex;
  justify-content: space-between;
  width: 90%;
  margin: auto;
  margin-top: 10px;
}
.tavi img {
  height: 22px;
}
.tavi p{
    position: relative;
    right: 10px;
}
.tavi button {
  background: none;
  color: orange;
  position: relative;
  bottom: 8px;
}
</style>
