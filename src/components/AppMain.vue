<template>
  <main>
    <div class="container">
      <h2>Film</h2>
      <CardMaker v-for="item in filmsArray" :key="item.id" :object="item" />
      <h2>Serie Tv</h2>
      <CardMaker v-for="item in seriesArray" :key="item.id" :object="item" />
    </div>
  </main>
</template>

<script>
import CardMaker from "./CardMaker.vue";

export default {
  name: "AppMain",
  components: {
    CardMaker,
  },

  props: {
    filmsArray: Array,
    seriesArray: Array,
  },

  data: function () {
    return {};
  },
};
</script>

<style lang="scss" scoped>
main {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: calc(100vh - 102px);
  background-color: black;
}

.container {
  display: flex;
  justify-content: flex-start;
  flex-wrap: wrap;
  padding: 1rem;
  width: 98%;
  height: 98%;
}

h2 {
  width: 100%;
  font-size: 2rem;
  margin: 1rem;
  color: white;
}
</style>
