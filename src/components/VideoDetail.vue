<template>
    <div v-if="video">
        <div>
            <iframe v-bind:src="videoUrl" />
        </div>
        <h3>{{ video.snippet.title }}</h3>
        <p>{{ video.snippet.description }}</p>
    </div>
</template>

<script>
export default {
    name: 'VideoDetail',
    props: ['video'],
    computed: {
        videoUrl() {
            //the below 'this.video.id.videoId' comes from the prop, whose object structure can be checked from the XHR request on the network tab on browser dev tools
            const videoId = this.video.id.videoId;
            return 'https://www.youtube.com/embed/' + videoId;
        }
    }
}
</script>