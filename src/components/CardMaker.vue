<template>
  <li class="card">
    <!-- Front-card -->
    <section class="front">
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
    </section>

    <!-- Retro-card -->
    <section class="retro hide">
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
        {{ object.overview ? object.overview : "Overview non disponibile!"}}
      </div>

      <!-- Attori -->
      <div>
        <h3>Actors:</h3>
        <ul>
          <li v-for="(item, index) in actorsArray" :key="index">{{ item.name }}</li>
        </ul>
      </div>

      <!-- Generi -->
      <div>
        <h3>Generi:</h3>
        <ul>
          <li v-for="(item, index) in object.genre_ids" :key="index"><h6>Genere {{ index + 1 }}: </h6> {{ item }}</li>
        </ul>
      </div>
    </section>
  </li>
</template>

<script>
import axios from "axios";

export default {
  name: "CardMaker",

  props: {
    object: Object,
  },

  data: function () {
    return {
      vote: Math.ceil(this.object.vote_average / 2),
      voidStar: 5 - Math.ceil(this.object.vote_average / 2),

      apikey: "6b6f49a0543af0887649fa643a8df95b",

      actorsArray: [],
      movieGenresArray: [],
      tvGenresArray: [],
    };
  },

  created: {
    
  },

  // {
  //   "id": 10759,
  //   "name": "Action & Adventure"
  // },

  mounted() {
    const options = {
        params: {
          api_key: this.apikey,
          query: "ciao",
        },
      };

      let type = 'tv';
      if (this.object.type === 'movie') {
        type = 'movie';
      }

      axios
        .get(`https://api.themoviedb.org/3/${type}/${this.object.id}/credits`, options)
        .then((response) => {
          let movieCast = response.data.cast;
          this.actorsArray = movieCast.slice(0, 5);
        })
      ;

      axios
        .get("https://api.themoviedb.org/3/genre/movie/list", options)
        .then((response) => {
          this.movieGenresArray = response.data.genres;
        })
      ;

      axios
        .get("https://api.themoviedb.org/3/genre/tv/list", options)
        .then((response) => {
          this.tvGenresArray = response.data.genres;
        })
      ;
  },
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

h6 {
  font-size: .8rem;
  color: #865556;
}
</style>
