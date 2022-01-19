<template>
    <SearchBar v-on:termChange="onTermChange"></SearchBar>
</template>

<script>
import SearchBar from './components/SearchBar';
export default {
    name: 'App',
    components: {
        SearchBar
    },
    methods: {
        //the searchTerm below is the 2nd argument from the 'onInput' function in SearchBar.vue
        onTermChange(searchTerm) {
            console.log(searchTerm);
        }
    }
};
</script>