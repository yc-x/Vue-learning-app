<template>
    <base-card>
        <base-button @click="switchTab('stored-resources')" 
        :mode="storedResButtonMode">Stored Resources</base-button>
        <base-button @click="switchTab('add-resources')"
        :mode="addResButtonMode"
        >Add Resource</base-button>
        <!-- onclick event "fallthrough" to the root element -->
    </base-card>  
    <keep-alive>
        <component :is="selectedTab"></component>
    </keep-alive>
</template>


<script>
import AddResources from './AddResources.vue';
import StoredResources from './StoredResources.vue';

export default{
    components: {
        AddResources, StoredResources
    },
    data(){
        return {
            selectedTab: 'stored-resources',
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
    },
    provide(){
        return {
            resources: this.storedResources,
            addResource: this.addResource,
            removeResource: this.removeResource,
        }
    },
    computed:{
        storedResButtonMode(){
            return this.selectedTab === 'stored-resources' ? null : 'flat';
        },
        addResButtonMode(){
            return this.selectedTab === 'add-resources' ? null : 'flat'
        },

    },
    methods:{
        switchTab(tab){
            this.selectedTab = tab;
        },
        addResource(title, description, url){
            var collectedResources = {
                id: new Date().toISOString(),
                title: title,
                description: description,
                link: url,
            };
            this.storedResources.unshift(collectedResources);
            this.selectedTab = 'stored-resources';  // after we add a new resource, we switch to resources tab.
        },
        removeResource(resourceID){
            var deleteIndex = this.storedResources.findIndex(res => res.id = resourceID);
            this.storedResources.splice(deleteIndex, 1);
        }
    }
}
</script>