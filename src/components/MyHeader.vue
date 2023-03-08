<template>
    <header>
        <!-- debug -->
        <!-- $emit('search', $event.target.value) -->
        <!-- @click.prevent="$emit('search', inputValue)" -->
        <input type="text" placeholder="Scrivi qui per cercare" v-model="query" />
        <button @click.prevent="getArray">Cerca</button>
    </header>
</template>
  
<script>
import Axios from "axios";

export default {
    name: "MyHeader",
    data() {
        return {
            query: "",
            listFilm: [],
            listTv: [],
            apiUrlFilm:
                "https://api.themoviedb.org/3/search/movie?api_key=2727abe6f9cfef8ece88aac30548b0e1&language=en-US&page=1&include_adult=false",
            apiUrlTv:
                "https://api.themoviedb.org/3/search/tv?api_key=2727abe6f9cfef8ece88aac30548b0e1&language=en-US&page=1&include_adult=false",
        };
    },
    methods: {
        // funzione che mi ritorna l'array di film e serie tv
        getArray() {
            // chiamata axios che mi torna i film
            Axios.get(`${this.apiUrlFilm}&query=${this.query}`).then((res) => {
                this.listFilm = res.data.results;
                console.log("axios mi torna questi film:", this.listFilm);
                this.$emit("searchFilm", this.listFilm);
            });
            // https://api.themoviedb.org/3/search/tv?api_key=2727abe6f9cfef8ece88aac30548b0e1&language=en-US&page=1&include_adult=false
            // chiamata axios che mi torna i le serie tv
            Axios.get(`${this.apiUrlTv}&query=${this.query}`).then((res) => {
                this.listTv = res.data.results;
                console.log("axios mi torna queste serie tv:", this.listTv);
                this.$emit("searchTv", this.listTv);
            });
        },
    },
};
</script>
  

<style scoped lang="scss">
header {
    background-color: brown;
    padding: 50px;
}
</style>