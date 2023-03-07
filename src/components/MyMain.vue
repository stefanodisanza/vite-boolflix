
<template>
    <main>
        <div class="container-card" v-for="film, i in details" :key="i">
            <div class="card">
                <div> Titolo: {{ film.title }}</div>
                <div>Titolo Originale: {{ film.original_title }}</div>
                <div>Lingua: {{ film.original_language }}</div>
                <div>Voto: {{ film.vote_average }}</div>
            </div>
        </div>
    <!-- <ul>
            <li >
              <div>{{film.title}}</div>
              <div>{{film.original_title}}</div>
              <div>{{film.original_language}}</div>
              <div>{{film.vote_average}}</div>
            </li>
                    </ul> -->
    </main>
</template>

<script>
// import Axios from 'axios'
export default {
    name: 'MyMain',
    props: {
        details: Array
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