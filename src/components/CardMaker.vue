<template>
  <ul class="card">
      <li>Titolo: {{ filmsItem.title }}</li>
      <li>Titolo Originale: {{ filmsItem.original_title }}</li>
      <li>Lingua: {{ filmsItem.original_language }}</li>
      <li>Voto: {{ filmsItem.vote_average }}</li>
  </ul>
</template>

<script>
export default {
  name: "CardMaker",

  props: {
    filmsItem: Object,
  },

  data: function () {
    return {
      
    };
  },
};
</script>

<style lang="scss" scoped>

.card {
  border: 1px solid #e2090c;
  color: white;
  height: 300px;
  width: 200px;
  margin: 0 1rem;
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
