<template>
  <main>
    <div class="container">
      <CardMaker v-for="(item, index) in filmsArray" :key="index" :filmsItem="item" />
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
</style>
