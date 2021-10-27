<template>
  <base-card>
    <base-button 
        @click="setSelectedTab('store-resource')"
        :mode="activeTabResource"
        >
        Stored Resources
    </base-button>
    <base-button 
        @click="setSelectedTab('add-resource')"
        :mode="activeTabAddResource"
        >Add Resources
    </base-button>
  </base-card>
  <component :is="selectedTab"></component>
</template>

<script>
import StoreResource from './StoredResource.vue';
import AddResource from './AddResource.vue';
export default {
    components: {
        StoreResource,
        AddResource
    },
    data(){
        return {
            selectedTab: 'store-resource',
            storedResources: [
                { id: 'Official-guide', title: 'Official Guide', description: 'The Official Vue.js Documentation', link: 'https://vuejs.org' },
                { id: 'stack-overflow', title: 'Stack Overflow', description: 'The Site you can use to find anything in your problem', link: 'https://vuejs.org' },
            ]
        }
    },
    computed: {
        activeTabResource(){
            return this.selectedTab === 'store-resource' ? null : 'flat'
        },
        activeTabAddResource(){
            return this.selectedTab === 'add-resource' ? null : 'flat'
        }
    },
    methods: {
        setSelectedTab(tab){
            console.log(tab)
            this.selectedTab = tab
        }
    },
    provide(){
        return {
            resources: this.storedResources
        }
    }
}
</script>

<style>

</style>