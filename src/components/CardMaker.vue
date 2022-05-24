<template>
  <ul class="card">
      <li><h3>Titolo:</h3> {{ object.title ? object.title : object.name }}</li>
      <li><h3>Titolo Originale:</h3> {{ object.original_title ? object.original_title : object.original_name }}</li>
      <li>
        <div v-if="object.original_language === 'it'">
          <h4>Lingua: </h4><span :class="`fi fi-it`"></span>
        </div>
        <div v-else-if="object.original_language === 'es'">
          <h4>Lingua: </h4><span :class="`fi fi-es`"></span>
        </div>
        <div v-else-if="object.original_language === 'en'">
          <h4>Lingua: </h4><span :class="`fi fi-gb`"></span>
        </div>
        <div v-else-if="object.original_language === 'ja'">
          <h4>Lingua: </h4><span :class="`fi fi-jp`"></span>
        </div>
        <div v-else-if="object.original_language === 'fr'">
          <h4>Lingua: </h4><span :class="`fi fi-fr`"></span>
        </div>
        <div v-else>
          <h4>Lingua: </h4>{{ object.original_language }}
        </div>
      </li>
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
