<template>
    <div>
        <SearchBar v-on:termChange="onTermChange"></SearchBar>
        <VideoList v-bind:videos="videos"></VideoList>
    </div>
</template>

<script>
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';

import axios from 'axios';
const API_KEY = 'XXX'; //get from google dev console

export default {
    name: 'App',
    components: {
        SearchBar,
        VideoList
    },
    data() {
        return {
            videos: []
        };
    },
    methods: {
        //the searchTerm below is the 2nd argument from the 'onInput' function in SearchBar.vue
        onTermChange(searchTerm) {
            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params: {
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchTerm
                }
            }).then(response => {
                console.log(response);
                this.videos = response.data.items;
                //the data.items object variables can be found by console logging the response object
            });
        }
    }
};
</script>