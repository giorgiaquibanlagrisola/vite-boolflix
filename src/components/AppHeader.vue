<script>
import { store } from '../store.js';

export default {
    data() {
        return {
            store

        };
    },
    methods: {

    }
}
</script>

<template>
    <header>
        <input v-model="store.searchText" type="text" placeholder="Nome di un film...">
        <button @click="$emit('startSearch')">
            Cerca
        </button>
    </header>
</template>

<style lang="scss" scoped>
</style>
