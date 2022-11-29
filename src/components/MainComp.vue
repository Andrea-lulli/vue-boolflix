<template>
  <div class="conteiner" >
    <CardComp v-for="(elem, index) in CardFilm"
          :key="index"
          :CardFilm="elem"/>
  </div>
</template>

<script>
import CardComp from "./CardComp.vue";

export default {
  name: "MainComp",

  components: {
    CardComp,
  },
   props: {
    CardFilm: Array,
    
  },

};
</script>

<style lang="scss" scoped>
.conteiner{
    display: flex;
    flex-wrap: wrap;
    width: 80%;
    margin: 0 auto;
    justify-content: space-between;
   
}
</style>