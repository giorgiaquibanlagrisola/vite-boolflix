<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';
import axios from 'axios';
import { store } from './store.js';

export default {
    data() {
        return {
            store,
        };
    },
    components: {
        AppHeader,
        AppMain
    },  
    methods: {
        search() {
            axios
              .get('https://api.themoviedb.org/3/search/movie', {
                    params: { 
                        api_key: 'e620333bf5f2944d736796855c58a280',
                       query: this.store.searchText
                    }
                })
                .then((response) => {
                    console.log(response.data.results);

                    this.store.movies = response.data.results;
                })
        }
    }
}
</script>

<template>
    <AppHeader @startSearch="search()" />
    <AppMain  />
</template>

<style lang="scss">
@use "assets/scss/main" as *;
@import "assets/scss/partials/reset";
</style>
