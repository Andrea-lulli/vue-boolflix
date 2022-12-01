<template>
  <div class="card-singole">
    <!-- poster dei film  -->
    <div class="card-front">
      <img
        class="card-noimage"
        v-if="CardSerie.backdrop_path == null"
        src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAJYAAACWCAMAAAAL34HQAAAAZlBMVEX///9NTU1JSUn09PSBgYFzc3M9PT2ysrJvb29ERETm5uaoqKhWVlbT09P8/PxqampcXFzJycnd3d3CwsIqKiqHh4fs7OxlZWV6enqVlZWhoaE3NzePj48AAAAyMjK6urohISEWFhZi2q6UAAAFB0lEQVR4nO2ai5aqIBRAwQcK6hFB8dVo/f9PXtSeptM0YdO6i73WNFYYu8PhhA+ELBaLxWKxWCwWi8VisVgsFst7ARlsgoTXtKqWbEBbvaaFPAdvgOO9ZjVqmY6VGS0eGYab0HL8F/NgDviOCa3QNWJzxg2NaPmmtcxEy2r9GKv1DFbrGda14Pj3NBtHC+B3XptqQeBVO/mbj9xSK8tb7NCuFB+llRwXTrT8KC1Oj16k+SAt1p3Xmc+Xj+20ZHte/3L2iVrOJ2mp9uEgqtWitmHKp6eU74Ll/SAWf6DFjlORVEtKmoLgP9BCwskpJftCLXUOKCO4XYnjxr+JSbOLltMdptwjKz9Nf7ew2Q1D7ODlUdx8YQMr2ROQ6ZepWHz/T6KlTRQ9nrhYHsY/0oLqVD0wUZ+j1Z+tMPUWhnEbrUcLUtZenXtaWmBsoiWKb8SGaXB7RozcrxO30GKka9Ym4OgV0dsTdfyu4G6gpUoH0+wbK7fDt9DdvJFpLd0pHtI5X1/Au+HdSc1czgqc8Wi509R30sVfwoGAzq3uh9G0lntawdNwpTXL763uDkMMa4F3KZPjvJ9FDE7RnNP2aLtBhPCqTxIsWKGmXbLS8UquG5rVqsl1T7oe3dUJQZatMOWbaXmzPmN2V4/S1UsLpL5qa1IruqtHN2mvl8moWQvW0Pqq1hnUWsiamwhokrn4NQ651GRzWv1SLtP+uiHcF9Kbxpdib0zLLRe7PFwfc+2+GcIxuNE40ka1lpPZ4ZdV3uosvMTrNEe21sI0PkVL8YcX+Jz0mF6ba13Svl4s77Mv0bxLC7fNsHhHyf6xFcZd8i4tTIauVqbEHKd036WFsV58FQ/zfYL6b9PSy5ZvC+kNefa2aFG//KkVHmP7Hi38zLV/J32b1lPoqfuJWrqo/vda368OntIKDWqV1BilOS1IDAJmtHAomFFEaObWn5jHBuGxoTuSniqYj5Mem9CizgbQF7WgTsMNSOvfXOS+0nI3wvDNVxaLOWY3rfw4V+H4ANfPf3f7ywJJ5SJxuXsVfDEetMOpA5gO4cf+p21Al1e8hFXTq8l4QUPurk1foO92+jBQf5A7msCOjSeOwZ26n7bgfMPN9GzcdvXhVy2GffWLSLZIP0YYnd9/AUA9oSLJAdW8YuN1JiYbL5VeKpDkZY9UUQY7l/lcDv3JsoxcT79VQRPrJsWwryp57WZOHfcoiJFI+fqJ/R8j0zoWOWripO6GiOxFtBcFTSrueokkKiyZ3txHyXi2vsqyg1sUCAeiUoUPJNNaUcD2+r9M9knAXdqL9hd35sy1YkZrAn6E2HD9BnIRxagJUcN1upRY0V5Hje0rbz9cmxa7NFdZLIgA6ccVooOWqv0uywhCtA+4cLxi3z/s9rEW6nMClc6wnE1aHDW+1mIHIaiKa72pDhmTSqfTQapOIc491LQQDVoiV7xBbZZ1LupkUDKSDE1fzfpef0t8gGRfOdXwYV9Cp21dohqzvA470XchLyHlBR3mxKHwvwRqvjIU5Tq5QI/clyr93aHP9qGPVeQgvyzi17WY1H866CLIxvkjlciQSNDwGCn9TIqeuyCHq/ygX2IZQ67UNUEGTIJUqkduk4hEZbo5YhmCIHrd6sg0qZdKTk3reAfnNuPG7bWn210A3bR9UetYP88l51Q+ESSBvPR2bDptnL8GnPef1XyLxWKxWCwWi8VisVgsFovF8j7+AbUKZIWoaiawAAAAAElFTkSuQmCC"
      />
      <img
        v-else
        :src="`http://image.tmdb.org/t/p/w342/${CardSerie.backdrop_path}`"
        class=""
        alt="..."
      />
    </div>

    <!-- copnteiner bandiere e stelle -->
    <div class="card-end">
      <!-- titolo -->
      <p class="titolo"> <strong class="">Titolo:</strong>  {{ CardSerie.name }}</p>

      <!-- bandiere  -->
      <span><strong>Lingua:</strong></span>
      <img
        class="bandiera"
        v-if="LinguaFilmSerie.includes(CardSerie.original_language)"
        :src="`/img/${CardSerie.original_language}.png`"
        alt=""
      />
      <img class="bandiera" v-else :src="`/img/ue.png`" alt="" />

      <!-- voto con stelle -->
      <div class="d-flex">
        <p> <strong>Voto:</strong> </p>
        <div class="voto mx-2" v-for="(elem, index) in votiserie" :key="index">
          &#9733;
        </div>
        <span
          class="stelle-vuote mx-2"
          v-for="(elem, index) in votimancanti"
          :key="index + 55"
        >
          &#9734;
        </span>
      </div>

      <!-- descrizione film  -->
      <!-- descrizione film  -->
      <p class="descrizione" v-if="CardSerie.overview == '' "><strong>Overview:</strong>  Nessuna Descrizione</p>
      <p class="descrizione" v-else><strong>Overview:</strong>  {{ CardSerie.overview }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardSerieComp",
  props: {
    CardSerie: Object,
  },
  data() {
    return {
      LinguaFilmSerie: ["en", "it", "de", "es", "ja", "fr"],
      votoFilm: "",
      votiserie: "",
      votimancanti: "",
    };
  },
  mounted() {
    this.votiserie = Math.round(this.CardSerie.vote_average / 2);
    this.votimancanti = 5 - this.votiserie;
  },
};
</script>


<style lang="scss" scoped>
div {
  img {
    width: 100%;
  }
}

.card-singole {
  width: calc((100% / 3) - 20px);
  margin: 20px 0;
  color: white;
  gap: 20px;
  position: relative;
  border: 2px solid white ;
}

.bandiera {
  width: 15%;
  margin: 5px 10px;
}
.titolo {
  font-size: 18px;
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
.card-end {
  display: none;
  position: absolute;
  top: 0;
  left: 0;
  padding: 7px;
}

.card-front {
  background-color: white;
}

.card-noimage {
  width: 56.2%;
  display: block;
  margin-left: auto;
  margin-right: auto;
  object-fit: cover;
  background-color: white;
}

.card-singole:hover .card-front {
  display: none;
}

.card-singole:hover .card-end {
  display: block;
  height: 100%;
  overflow: auto;
}
::-webkit-scrollbar {
  width: 0.8em;
  height: 0.8em;
  background: black;
  margin-right: 10px;
}
::-webkit-scrollbar:hover {
  background-color: black;
  border: none;
}
</style>
