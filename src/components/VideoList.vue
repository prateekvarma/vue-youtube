<template>
    <ul>
        <VideoListItem 
        v-for="(video, index) in videos" 
        v-bind:video="video"
        :key="index"
        @videoSelect="onVideoSelect"
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
    props: ['videos'],
    methods: {
        onVideoSelect(video) {
            //Note that the 'videoSelect' is not the same as the @videoSelect above, because it is a completely new event variable that is being emitted to it's own parent component
            //Also, the 'video' variable does not need the 'this' prefix, because it is not coming from props, but rather just being passed from it's child component.
            this.$emit('videoSelect', video);
        }
    }
};
</script>

<style>
</style>