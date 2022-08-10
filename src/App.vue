<template>
    <the-header :title="title"></the-header>
    <stored-resources :resources="storedResources"></stored-resources>
</template>

<script>
import StoredResources from './components/LearningResource/StoredResources.vue';
import TheHeader from './components/layout/TheHeader.vue';

export default {
    components: {
        StoredResources, TheHeader
    },
    data(){
        return {
            title: 'title!!',
            storedResources: [
                {
                    id: '0',
                    title: 'Official Guide',
                    description: 'The official documentation.',
                    link: 'https://vuejs.org',
                },
                {
                    id: '1',
                    title: 'Google',
                    description: 'Go to Google!',
                    link: 'https://google.com',
                }
            ]
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