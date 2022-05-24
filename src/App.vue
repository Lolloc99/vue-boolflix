<template>
  <div>
    <AppHeader @search="userResearch($event)" />
    <AppMain :filmsArray="filmsArray" :seriesArray="seriesArray" />
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    AppHeader,
    AppMain,
  },

  data: function () {
    return {
      filmsArray: [],
      seriesArray: [],
    };
  },

  methods: {
    userResearch(event) {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "6b6f49a0543af0887649fa643a8df95b",
            query: event,
          },
        })
        .then((resp) => {
          this.filmsArray = resp.data.results;
          console.log(this.filmsArray);
        });

      axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: {
            api_key: "6b6f49a0543af0887649fa643a8df95b",
            query: event,
          },
        })
        .then((resp) => {
          this.seriesArray = resp.data.results;
          console.log(this.seriesArray);
        });
    },
  },
};
</script>

<style lang="scss">
@import "./style/common.scss";
</style>
