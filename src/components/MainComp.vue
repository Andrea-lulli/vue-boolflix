<template>
  <div class="conteiner">
    <!-- titolo film -->
    <div class="col-12 text-center titolo">
      <h1>Film</h1>
    </div>

    <!-- card film -->
    <CardComp v-for="(elem, index) in CardFilm" :key="index" :CardFilm="elem" />

    <!-- titolo serie tv -->
    <div class="col-12 text-center titolo">
      <h1>Serie TV</h1>
    </div>
    <!-- card serie tv  -->
    <CardSerieComp v-for="elem in CardSerie" :key="elem.id" :CardSerie="elem" />
  </div>
</template>

<script>
import CardComp from "./CardComp.vue";
import CardSerieComp from "./CardSerieComp.vue";

export default {
  name: "MainComp",

  components: {
    CardComp,
    CardSerieComp,
  },

  props: {
    CardFilm: Array,
    CardSerie: Array,
  },
};
</script>

<style lang="scss" scoped>
.conteiner {
  display: flex;
  flex-wrap: wrap;
  width: 80%;
  margin: 0 auto;
  justify-content: space-between;
}
.titolo {
  color: white;
  margin: 20px 0;
}
</style>