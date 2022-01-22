<template>
    <div>
        <SearchBar v-on:termChange="onTermChange"></SearchBar>
        <VideoDetail v-bind:video="selectedVideo"></VideoDetail>
        <VideoList v-bind:videos="videos" @videoSelect="onVideoSelect"></VideoList>
    </div>
</template>

<script>
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';

import axios from 'axios';
const API_KEY = 'XXX'; //get from google dev console

export default {
    name: 'App',
    components: {
        SearchBar,
        VideoList,
        VideoDetail
    },
    data() {
        return {
            videos: [],
            selectedVideo: null
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
                this.videos = response.data.items;
                //the data.items object variables can be found by console logging the response object
            });
        },
        onVideoSelect(video) {
            this.selectedVideo = video;
        }
    }
};
</script>