<template>
  <li class="card">
    <!-- Front-card -->
    <div class="front">
      <img
        v-if="object.poster_path"
        :src="`http://image.tmdb.org/t/p/w300/${object.poster_path}`"
        :alt="object.title ? object.title : object.name"
      />
      <img
        v-else
        src="../assets/img/no_poster.jpg"
        alt="Poster_not_available"
      />
    </div>

    <!-- Retro-card -->
    <div class="retro hide">
      <!-- Titolo -->
      <div>
        <h3>Titolo:</h3>
        {{ object.title ? object.title : object.name }}
      </div>

      <!-- Titolo Originale -->
      <div>
        <h3>Titolo Originale:</h3>
        {{
          object.original_title ? object.original_title : object.original_name
        }}
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
        <span class="gold" v-for="(item, index) in this.vote" :key="'A' + index"
          ><i class="fas fa-star"></i
        ></span>
        <span v-for="(item, index) in this.voidStar" :key="'B' + index"
          ><i class="fas fa-star"></i
        ></span>
      </div>

      <!-- Overview -->
      <div>
        <h3>Overview:</h3>
        {{ object.overview }}
      </div>
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
  min-width: calc(100% / 5 - 2.8rem);
}

li {
  display: flex;
  flex-direction: column;
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
  font-size: 1rem;
  margin: 0.3rem 0;
}

.front {
  min-height: 452px;

  img {
    width: 300px;
  }
}

.retro {
  max-width: 300px;
  min-width: 300px;
  max-height: 452px;
  min-height: 452px;
  overflow-y: auto;
}

li:hover .retro {
  display: block;
}

li:hover .front {
  display: none;
}

.gold {
  color: gold;
}

.hide {
  display: none;
}

h3,
h4,
h5 {
  color: #9e0b0d;
}
</style>
