<template>
  <ul class="card">
      <li>Titolo: {{ object.title ? object.title : object.name }}</li>
      <li>Titolo Originale: {{ object.original_title ? object.original_title : object.original_name }}</li>
      <!-- <li class="fib fi-gr"></li> -->
      <!-- <li><span class="fi fi-gr"></span></li> -->
      <li>Lingua: {{ object.original_language }}</li>
      <li>Voto: {{ object.vote_average }}</li>
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
