<template>
    <main>
        <!-- film -->
        <div class="container-card" v-for="film in listFilm" :key="film.id">
            <div class="card">
                <div class="cover">
                    <img v-if="film.poster_path !== null" :src="coverUrl + film.poster_path" :alt="film.title" />
                    <img v-else class="cover-netflix"
                        src="https://i.pinimg.com/564x/01/e1/35/01e135a5bcabe81ce279076de8dfbfd9.jpg" alt="">
                    <!-- container info -->
                    <div class="container-info">
                        <div>Titolo: {{ film.title }}</div>
                        <div>Titolo Originale: {{ film.original_title }}</div>
                        <div class="language">Lingua: <img class="mini_flag" :src="insertFlag(film.original_language)" />
                        </div>
                        <!-- contenitore del voto -->
                        <div>
                            Voto:
                            <span v-for="star, i in arrayStar" :key="i">
                                <i v-if="i > (film.vote_average / 2) - 1" class="far fa-star"></i>
                                <i v-else class="star" :class="star"></i>
                            </span>
                        </div>
                        <!-- //contenitore del voto -->
                    </div>
                </div>
            </div>
        </div>
        <!-- serie tv -->
        <!-- poster_path -->
        <div class="container-card" v-for="tv in listTv" :key="tv.id">
            <div class="card">
                <div class="cover">
                    <img class="cover-img" v-if="tv.poster_path !== null" :src="coverUrl + tv.poster_path"
                        :alt="tv.title" />
                    <img v-else class="cover-netflix"
                        src="https://i.pinimg.com/564x/01/e1/35/01e135a5bcabe81ce279076de8dfbfd9.jpg" alt="">
                    <!-- container info -->
                    <div class="container-info">
                        <div>Titolo: {{ tv.name }}</div>
                        <div>Titolo Originale: {{ tv.original_name }}</div>
                        <div class="language">Lingua: <img class="mini_flag" :src="insertFlag(tv.original_language)" />
                        </div>
                        <!-- contenitore del voto -->
                        <div>
                            Voto:
                            <span v-for="star, i in arrayStar" :key="i">
                                <i v-if="i > (tv.vote_average / 2) - 1" class="far fa-star"></i>
                                <i v-else class="star" :class="star"></i>
                            </span>
                        </div>
                        <!-- //contenitore del voto -->
                    </div>
                </div>
            </div>
        </div>
    </main>
</template>
<script>
const itFlag = '/it_flag.png';
const enFlag = '/en_flag.png';
const frFlag = '/fr_flag.png';

export default {
    name: "MyMain",
    props: {
        listFilm: Array,
        listTv: Array,
    },
    data() {
        return {
            coverUrl: "http://image.tmdb.org/t/p/w342",
            itFlag: itFlag,
            enFlag: enFlag,
            frFlag: frFlag,
            arrayStar: [
                'fas fa-star',
                'fas fa-star',
                'fas fa-star',
                'fas fa-star',
                'fas fa-star',
            ]
        };
    },
    methods: {
        insertFlag(item) {
            if (item === 'it') {
                return this.itFlag;
            } else if (item === 'en') {
                return this.enFlag;
            } else if (item === 'fr') {
                return this.frFlag;
            } else {
                return 'https://www.unr.edu/main/images/news/blog/progress-flag.jpg';
            }
        },
    },
};
</script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
main {
    margin: 20px auto;
    width: 70%;
    display: flex;
    flex-wrap: wrap;
}

.container-card {
    padding: 20px;
    // debug
    height: 100%px;
    width: 20%;
    background-color: #2c3e50;
    border: 1px solid black;
    color: black;

}

.card {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
    height: 100%;
}

.cover-img {
    height: 500px;
}

.cover-netflix {
    width: 342px;
    height: 100%;
}

.star {
    color: yellow;
}

.none {
    display: none;
}

img {
    width: 100%;
}

.mini_flag {
    width: 15px;
}
</style>