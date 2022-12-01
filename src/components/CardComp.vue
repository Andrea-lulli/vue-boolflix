<template>
  <div class="card-singole">

    <!-- poster dei film  -->
    <img
      class=""
      v-if="CardFilm.backdrop_path == null"
      src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAJYAAACWCAMAAAAL34HQAAAAZlBMVEX///9NTU1JSUn09PSBgYFzc3M9PT2ysrJvb29ERETm5uaoqKhWVlbT09P8/PxqampcXFzJycnd3d3CwsIqKiqHh4fs7OxlZWV6enqVlZWhoaE3NzePj48AAAAyMjK6urohISEWFhZi2q6UAAAFB0lEQVR4nO2ai5aqIBRAwQcK6hFB8dVo/f9PXtSeptM0YdO6i73WNFYYu8PhhA+ELBaLxWKxWCwWi8VisVgsFst7ARlsgoTXtKqWbEBbvaaFPAdvgOO9ZjVqmY6VGS0eGYab0HL8F/NgDviOCa3QNWJzxg2NaPmmtcxEy2r9GKv1DFbrGda14Pj3NBtHC+B3XptqQeBVO/mbj9xSK8tb7NCuFB+llRwXTrT8KC1Oj16k+SAt1p3Xmc+Xj+20ZHte/3L2iVrOJ2mp9uEgqtWitmHKp6eU74Ll/SAWf6DFjlORVEtKmoLgP9BCwskpJftCLXUOKCO4XYnjxr+JSbOLltMdptwjKz9Nf7ew2Q1D7ODlUdx8YQMr2ROQ6ZepWHz/T6KlTRQ9nrhYHsY/0oLqVD0wUZ+j1Z+tMPUWhnEbrUcLUtZenXtaWmBsoiWKb8SGaXB7RozcrxO30GKka9Ym4OgV0dsTdfyu4G6gpUoH0+wbK7fDt9DdvJFpLd0pHtI5X1/Au+HdSc1czgqc8Wi509R30sVfwoGAzq3uh9G0lntawdNwpTXL763uDkMMa4F3KZPjvJ9FDE7RnNP2aLtBhPCqTxIsWKGmXbLS8UquG5rVqsl1T7oe3dUJQZatMOWbaXmzPmN2V4/S1UsLpL5qa1IruqtHN2mvl8moWQvW0Pqq1hnUWsiamwhokrn4NQ651GRzWv1SLtP+uiHcF9Kbxpdib0zLLRe7PFwfc+2+GcIxuNE40ka1lpPZ4ZdV3uosvMTrNEe21sI0PkVL8YcX+Jz0mF6ba13Svl4s77Mv0bxLC7fNsHhHyf6xFcZd8i4tTIauVqbEHKd036WFsV58FQ/zfYL6b9PSy5ZvC+kNefa2aFG//KkVHmP7Hi38zLV/J32b1lPoqfuJWrqo/vda368OntIKDWqV1BilOS1IDAJmtHAomFFEaObWn5jHBuGxoTuSniqYj5Mem9CizgbQF7WgTsMNSOvfXOS+0nI3wvDNVxaLOWY3rfw4V+H4ANfPf3f7ywJJ5SJxuXsVfDEetMOpA5gO4cf+p21Al1e8hFXTq8l4QUPurk1foO92+jBQf5A7msCOjSeOwZ26n7bgfMPN9GzcdvXhVy2GffWLSLZIP0YYnd9/AUA9oSLJAdW8YuN1JiYbL5VeKpDkZY9UUQY7l/lcDv3JsoxcT79VQRPrJsWwryp57WZOHfcoiJFI+fqJ/R8j0zoWOWripO6GiOxFtBcFTSrueokkKiyZ3txHyXi2vsqyg1sUCAeiUoUPJNNaUcD2+r9M9knAXdqL9hd35sy1YkZrAn6E2HD9BnIRxagJUcN1upRY0V5Hje0rbz9cmxa7NFdZLIgA6ccVooOWqv0uywhCtA+4cLxi3z/s9rEW6nMClc6wnE1aHDW+1mIHIaiKa72pDhmTSqfTQapOIc491LQQDVoiV7xBbZZ1LupkUDKSDE1fzfpef0t8gGRfOdXwYV9Cp21dohqzvA470XchLyHlBR3mxKHwvwRqvjIU5Tq5QI/clyr93aHP9qGPVeQgvyzi17WY1H866CLIxvkjlciQSNDwGCn9TIqeuyCHq/ygX2IZQ67UNUEGTIJUqkduk4hEZbo5YhmCIHrd6sg0qZdKTk3reAfnNuPG7bWn210A3bR9UetYP88l51Q+ESSBvPR2bDptnL8GnPef1XyLxWKxWCwWi8VisVgsFovF8j7+AbUKZIWoaiawAAAAAElFTkSuQmCC"
    />
    <img
      v-else
      :src="`http://image.tmdb.org/t/p/w342/${CardFilm.backdrop_path}`"
      class="card-img-top"
      alt="..."
    />

    <!-- copnteiner bandiere e stelle -->
    <div class="card-body">

      <!-- bandiere  -->
      <p class="titolo">Titolo: {{ CardFilm.title }}</p>
      <img
        class="bandiera"
        v-if="LinguaFilm.includes(CardFilm.original_language)"
        :src="`/img/${CardFilm.original_language}.png`"
        alt=""
      />
      <img class="bandiera" v-else :src="`/img/ue.png`" alt="" />

      <!-- voto con stelle -->
      <div class="d-flex">
        <p>Voto:</p>
        <div class="voto mx-2" v-for="(elem, index) in votifilm" :key="index">
          &#9733;
        </div>
        <span
          class="stelle-vuote mx-2"
          v-for="(elem, inde) in votimancanti"
          :key="inde"
        >
          &#9734;
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardComp",
  props: {
    CardFilm: Object,
  },
  data() {
    return {
      LinguaFilm: ["en", "it", "de", "es", "ja", "fr"],
      votifilm: "",
      votimancanti: "",
    };
  },
  mounted() {
    this.votifilm = Math.round(this.CardFilm.vote_average / 2);
    this.votimancanti = 5 - this.votifilm;
  },

  methods: {},
};
</script>


<style lang="scss" scoped>
div {
  img {
    width: 100%;
    aspect-ratio: 3/2;
  }
}

.card-singole {
  width: calc((100% / 4) - 10px);
  margin: 10px 0;
  color: white;
  background-color: rgb(90, 88, 88);
  padding: 10px;
  gap: 10px;
}

.bandiera {
  width: 20%;
  margin: 5px 0;
}
.titolo {
  font-size: 12px;
}
.voto {
  margin: 0 2px;
  font-size: 18px;
  color: yellow;
}
.stelle-vuote {
  margin: 0 2px;
  font-size: 18px;
  color: white;
}
</style>