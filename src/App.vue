<template>
  <ul>
      <learning-resource 
        v-for="resource in storedResources" 
        :key="resource.id"  
        :title="resource.title"
        :description="resource.description"
        :link="resource.link"
      ></learning-resource>
  </ul>
</template>

<script>
import LearningResource from './components/learning-resource/LearningResource.vue';
export default {
    components: {
        LearningResource
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

</style>