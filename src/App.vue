<template>
    <the-header />
    <stored-resource :resources="storedResources"></stored-resource>
</template>

<script>
import StoredResource from './components/learning-resource/StoredResource.vue';
import TheHeader from './components/layout/TheHeader.vue';

export default {
    components: {
        StoredResource,
        TheHeader
    },
    data(){
        return {
            storedResources: [
                { id: 'Official-guide', title: 'Official Guide', description: 'The Official Vue.js Documentation', link: 'https://vuejs.org' },
                { id: 'stack-overflow', title: 'Stack Overflow', description: 'The Site you can use to find anything in your problem', link: 'https://vuejs.org' },
            ]
        }
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