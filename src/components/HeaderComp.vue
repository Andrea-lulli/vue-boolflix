<template>
  <div class="col-11 d-flex">
    <div class="col-8">
      <h2 class="text-light">Booflix</h2>
    </div>
    <div class="col-4">
      <input placeholder="Inserisci testo"
        type="Text"
        class="form-control"
        id="exampleInputEmail1"
        aria-describedby="emailHelp"
        v-model="search"
        @keyup="$emit('inputSearch' , search)"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "HeaderComp",
  props: {},
  data() {
    return {
      search: ""



    };
  },
};
</script>


<style scoped lang="scss">
</style>
