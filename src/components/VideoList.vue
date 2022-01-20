<template>
    <ul>
        <h4>Video List has {{ videos.length }} videos</h4>
    </ul>
</template>

<script>
export default {
    name: 'VideoList',
    props: ['videos']
};
</script>

<style>
</style>