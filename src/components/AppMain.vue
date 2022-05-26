<template>
  <main>
    <div class="container">
      <h2>Film</h2>
      <ul>
        <CardMaker v-for="item in filmsArray" :key="item.id" :object="item"/>
      </ul>
      <h2>Serie Tv</h2>
      <ul>
        <CardMaker v-for="item in seriesArray" :key="item.id" :object="item" />
      </ul>
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
  min-height: calc(100vh - 100px);
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
  font-size: 2rem;
  margin: 1rem;
  color: #9e0b0d;
  width: 100%;
}

ul {
  display: flex;
  flex-flow: row wrap;
}
</style>
