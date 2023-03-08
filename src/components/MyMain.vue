
<template>
    <main>
        <div class="container-card" v-for="film, i in listFilm" :key="i">
            <div class="card">
                <div> Titolo: {{ film.title }}</div>
                <div>Titolo Originale: {{ film.original_title }}</div>
                <div>Lingua: {{ film.original_language }}</div>
                <div>Voto: {{ film.vote_average }}</div>
            </div>
        </div>
        <div class="container-card" v-for="tv in listTv" :key="tv.id">
            <div class="card">
                <div> Titolo: {{ tv.name }}</div>
                <div>Titolo Originale: {{ tv.original_name }}</div>
                <div>Lingua: {{ tv.original_language }}</div>
                <div>Voto: {{ tv.vote_average }}</div>
            </div>
        </div>
    </main>
</template>

<script>
// import Axios from 'axios'
export default {
    name: 'MyMain',
    props: {
        listFilm: Array,
        listTv: Array,
    },
}
</script>

<style lang="scss" scoped>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
</style>