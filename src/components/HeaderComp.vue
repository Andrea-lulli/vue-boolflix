<template>
  <div>
    <div class="">
      <input
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
