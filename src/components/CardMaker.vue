<template>
  <li class="card">
    <!-- Immagine -->
    <div class="div-img">
      <img
        :src="`http://image.tmdb.org/t/p/w300/${
          object.poster_path ? object.poster_path : object.backdrop_path
        }`"
        :alt="object.title ? object.title : object.name"
      />
    </div>

    <!-- Titolo -->
    <div>
      <h3>Titolo:</h3>
      {{ object.title ? object.title : object.name }}
    </div>

    <!-- Titolo Originale -->
    <div>
      <h3>Titolo Originale:</h3>
      {{ object.original_title ? object.original_title : object.original_name }}
    </div>

    <!-- Lingua -->
    <div>
      <div v-if="object.original_language === 'it'">
        <h4>Lingua:</h4>
        <span :class="`fi fi-it`"></span>
      </div>
      <div v-else-if="object.original_language === 'es'">
        <h4>Lingua:</h4>
        <span :class="`fi fi-es`"></span>
      </div>
      <div v-else-if="object.original_language === 'en'">
        <h4>Lingua:</h4>
        <span :class="`fi fi-gb`"></span>
      </div>
      <div v-else-if="object.original_language === 'ja'">
        <h4>Lingua:</h4>
        <span :class="`fi fi-jp`"></span>
      </div>
      <div v-else-if="object.original_language === 'fr'">
        <h4>Lingua:</h4>
        <span :class="`fi fi-fr`"></span>
      </div>
      <div v-else>
        <h4>Lingua:</h4>
        {{ object.original_language }}
      </div>
    </div>

    <!-- Voto -->
    <div>
      <h5>Voto:</h5>
      <div v-if="this.vote != 0">
        <span class="gold" v-for="(item, index) in this.vote" :key="index"
          ><i class="fas fa-star"></i
        ></span>
        <span v-for="(item, index) in this.voidStar" :key="index"
          ><i class="fas fa-star"></i
        ></span>
      </div>
      <div v-else>Nessun voto</div>
    </div>
  </li>
</template>

<script>
export default {
  name: "CardMaker",

  props: {
    object: Object,
  },

  data: function () {
    return {
      vote: Math.ceil(this.object.vote_average / 2),
      voidStar: 5 - Math.ceil(this.object.vote_average / 2),
    };
  },

  methods: {},
};
</script>

<style lang="scss" scoped>
@import "~flag-icons/css/flag-icons.css";
@import "~@fortawesome/fontawesome-free/css/all.min.css";

.card {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  border: 1px solid #e2090c;
  color: white;
  margin: 1rem;
  padding: 0.4rem;
  max-width: 315px;
  min-width: 315px;
  min-height: 715px;
}

li {
  display: flex;
  flex-direction: column;
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
  font-size: 1rem;
  margin: 0.3rem 0;
}

.div-img {
  min-height: 452px;
}

.gold {
  color: gold;
}
</style>
