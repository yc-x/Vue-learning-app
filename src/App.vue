<template>
    <the-header :title="title"></the-header>
    <!-- <stored-resources :resources="storedResources"></stored-resources> -->
    <the-resource></the-resource>
</template>

<script>
// import StoredResources from './components/LearningResource/StoredResources.vue';
import TheHeader from './components/layout/TheHeader.vue';
import TheResource from './components/LearningResource/TheResource.vue';

export default {
    components: {
        TheHeader, TheResource
    },
    data(){
        return {
            title: 'title!!',
        };
    }
}
</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

    * {
        box-sizing: border-box;
    }

    html {
        font-family: 'Roboto', sans-serif;
    }

    body {
        margin: 0;
    }
</style>