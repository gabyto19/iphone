<template>
  <div class="fav">
    <p>Favourites</p>
    <h3>No Favourites</h3>
  </div>
  <div class="spacer">

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
.spacer{
  height: 251px;
}
.fav {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  height: 250px;
}

.fav p {
}
.fav h3{
  color: grey;
}
</style>
