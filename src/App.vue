<template>
  <div id="app">
    <HeaderComp @inputSearch="nomeMethods" />
    <MainComp />
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
    };
  },

  mounted() {
    axios
      .get(
        "https://api.themoviedb.org/3/movie/550?api_key=5e4cb44696283cc119534aa11856e842&query=" + this.SearchUtente)

      .then((resp) => {
        this.ListaFilm = resp.data;
      });
      
      
  },

  methods: {
    nomeMethods(search) {
      this.SearchUtente = search;
    },
  },
};
</script>

<style lang="scss">
</style>
