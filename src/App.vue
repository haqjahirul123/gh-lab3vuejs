<template>
    <div>
        <add-snippet></add-snippet> 
        <show-snippet></show-snippet>
    </div>
</template>

<script>
// Imports
import addSnippet from './components/addSnippet.vue';
import showAllSnippets from './components/showAllSnippets.vue';

export default {
    components: {
        'add-snippet': addSnippet,
        'show-snippet':showAllSnippets
    },
    data () {
        return {

        }
    },
    methods: {

    }
}
</script>

<style>
body{
    margin: 0;
    font-family: 'Nunito SemiBold';
}
</style>
