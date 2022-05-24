<template>
  <ul class="card">
      <li><h3>Titolo:</h3> {{ object.title ? object.title : object.name }}</li>
      <li><h3>Titolo Originale:</h3> {{ object.original_title ? object.original_title : object.original_name }}</li>
      <li><h4>Lingua: </h4>{{object.original_language}} <span :class="`fi fi-${object.original_language}`"></span></li>
      <li><h5>Voto:</h5> {{ object.vote_average }}</li>
  </ul>
</template>

<script>
export default {
  name: "CardMaker",

  props: {
    object: Object,
  },

  data: function () {
    return {
    };
  },

  methods: {
  },
};
</script>

<style lang="scss" scoped>
@import "~flag-icons/css/flag-icons.css";

.card {
  border: 1px solid #e2090c;
  color: white;
  height: 300px;
  width: calc(100% / 4 - 2rem);
  margin: 1rem;
  padding: 0.4rem;
}

ul {
  list-style: none;

  li {
    font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
      "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
    font-size: 1rem;
    margin: 0.3rem 0;
  }
}
</style>
