<template>
    <li>
        <img v-bind:src="video.snippet.thumbnails.default.url" />
        {{ video.snippet.title }}
    </li>
</template>

<script>
    export default {
        name: 'VideoListItem',
        props: ['video']
    }
</script>