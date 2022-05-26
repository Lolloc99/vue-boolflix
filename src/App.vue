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
      apikey: "6b6f49a0543af0887649fa643a8df95b",
      filmsArray: [],
      seriesArray: [],
    };
  },

  methods: {
    userResearch(event) {
      const options = {
        params: {
          api_key: this.apikey,
          query: event,
        },
      };

      axios
        .get("https://api.themoviedb.org/3/search/movie", options)
        .then((resp) => {
          this.filmsArray = resp.data.results;
          this.filmsArray.map((film) => {
            film.type = 'movie';
          });
          console.log('Films Array:', this.filmsArray);
        })
      ;

      axios
        .get("https://api.themoviedb.org/3/search/tv", options)
        .then((resp) => {
          this.seriesArray = resp.data.results;
          console.log('Series Array:', this.seriesArray);
        })
      ;      
    }
  },
};
</script>

<style lang="scss">
@import "./style/common.scss";
</style>
