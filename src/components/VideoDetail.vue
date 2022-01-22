<template>
    <div v-if="video">
        <h3>{{ video.snippet.title }}</h3>
        <p>{{ video.snippet.description }}</p>
    </div>
</template>

<script>
export default {
    name: 'VideoDetail',
    props: ['video']
}
</script>