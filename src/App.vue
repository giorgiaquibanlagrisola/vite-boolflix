<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';
import axios from 'axios';

export default {
    data() {
        return {
            searchText:'',
            movies: []

        }
    },
    components: {
        AppHeader,
        AppMain,
        AppFooter
    },  
    methods: {
        search() {
            axios
              .get('https://api.themoviedb.org/3/search/movie', {
                    params: { 
                        api_key: 'e620333bf5f2944d736796855c58a280',
                       query: this.searchText
                    }
                })
                .then((response) => {
                    console.log(response.data.results);

                    this.movies = response.data.results;
                })
        }
    }
}
</script>

<template>
    <header>
        <input v-model="searchText" type="text" placeholder="Nome di un film...">
        <button @click="search()">
            Cerca
        </button>
    </header>

    <main>
        <div>
            <ul>
                <li v-for="(movie, i) in movies" :key="i">
                    <div>
                        Title: {{ movie.title }}
                    </div>
                    <div>
                        Original title: {{ movie.original_title }}
                    </div>
                    <div>
                        Language: {{ movie.original_language }}
                    </div>
                    <div>
                        Voto: {{ movie.vote_average }}
                    </div>
                </li>
            </ul>
        </div>
    </main>

    <!--<AppHeader />

    <AppMain />

    <AppFooter />  -->
    
</template>

<style lang="scss">
@use "assets/scss/main" as *;
@import "assets/scss/partials/reset";
</style>
