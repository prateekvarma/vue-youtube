<template>
    <ul>
        <VideoListItem 
        v-for="(video, index) in videos" 
        v-bind:video="video"
        :key="index"
        >
        </VideoListItem>
    </ul>
</template>

<script>
import VideoListItem from './VideoListItem';
export default {
    name: 'VideoList',
    components: {
        VideoListItem
    },
    props: ['videos']
};
</script>

<style>
</style>