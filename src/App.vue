<template>
  <div id="app">
    <div class="row">
      <HeaderComp @inputSearch="nomeMethods" />
      <button class="col-1 button-cerca" @click="SceltaFilm(), SceltaSerie()">
        Cerca
      </button>
    </div>
    <MainComp :CardFilm="ListaFilm" :CardSerie="ListaSerie" />
  </div>
</template>

<script>
import HeaderComp from "./components/HeaderComp.vue";
import MainComp from "./components/MainComp.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    HeaderComp,
    MainComp,
  },

  data() {
    return {
      SearchUtente: "",
      ListaFilm: "",
      ListaSerie: "",
    };
  },

  mounted() {},

  methods: {
    nomeMethods(search) {
      this.SearchUtente = search;
    },

    SceltaFilm() {
      axios
        .get(
          `https://api.themoviedb.org/3/search/movie?api_key=5e4cb44696283cc119534aa11856e842&query=${this.SearchUtente}`
        )
        .then((resp) => {
          this.ListaFilm = resp.data.results;
           console.log(this.ListaFilm);
        });
    },

    SceltaSerie() {
      axios
        .get(
          `https://api.themoviedb.org/3/search/tv?api_key=5e4cb44696283cc119534aa11856e842&query=${this.SearchUtente}`
        )
        .then((resp) => {
        this.ListaSerie = resp.data.results; 
        console.log(this.ListaSerie);
         
        });
    },
  },
};
</script>


<style lang="scss">
body {
  background-color: rgb(6, 6, 6) !important;
}

.button-cerca {
  background-color: rgb(6, 6, 6);
  color: white;
  border: 1px solid white;
}
</style>
