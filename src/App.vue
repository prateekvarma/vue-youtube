<template>
    <SearchBar v-on:termChange="onTermChange"></SearchBar>
</template>

<script>
import SearchBar from './components/SearchBar';
import axios from 'axios';
const API_KEY = 'XXX'; //get from google dev console

export default {
    name: 'App',
    components: {
        SearchBar
    },
    methods: {
        //the searchTerm below is the 2nd argument from the 'onInput' function in SearchBar.vue
        onTermChange(searchTerm) {
            axios.get('https://googleapis.com/youtube/v3/search', {
                params: {
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchTerm
                }
            });
        }
    }
};
</script>