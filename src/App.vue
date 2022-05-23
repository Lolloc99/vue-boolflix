<template>
  <div>
    <AppHeader @search="userResearch" />
    <AppMain :filmsArray="filmsArray" />
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    AppHeader,
    AppMain,
  },

  data: function () {
    return {
      filmsArray: [],
    };
  },

  methods: {
    userResearch(searchText){
      return filteredInput
    }
  },

  created() {
    axios
      .get("https://api.themoviedb.org/3/search/movie", {
        params: {
          api_key: "6b6f49a0543af0887649fa643a8df95b",
          query: filteredInput,
        },
      })
      .then((resp) => {
        this.filmsArray = resp.data.results;
        console.log(this.filmsArray);
      });
  },
      
};
</script>

<style lang="scss">
@import "./style/common.scss";
</style>
