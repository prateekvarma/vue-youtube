<template>
    <li @click="onVideoSelect">
     <!-- Above the HTML click event is triggered, which runs the 'onVideoSelect' method, which in turn sends the particular video to be played - by emitting it as an event to it's parent component -->
        <img v-bind:src="video.snippet.thumbnails.default.url" />
        {{ video.snippet.title }}
    </li>
</template>

<script>
    export default {
        name: 'VideoListItem',
        props: ['video'],
        methods: {
            onVideoSelect() {
                this.$emit('videoSelect', this.video);
            }
        }
    }
</script>