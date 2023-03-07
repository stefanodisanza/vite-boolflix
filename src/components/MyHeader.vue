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
            apiUrl:
                "https://api.themoviedb.org/3/search/movie?api_key=2727abe6f9cfef8ece88aac30548b0e1",
        };
    },
    methods: {
        getArray() {
            Axios.get(`${this.apiUrl}&query=${this.query}`).then((res) => {
                this.listFilm = res.data.results;
                console.log("axios mi ritorna:", this.listFilm);
                this.$emit('search', this.listFilm)
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