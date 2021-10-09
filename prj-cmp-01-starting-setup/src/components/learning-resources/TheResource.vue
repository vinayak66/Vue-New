<template>
  <base-card>
    <base-button
      @click="setSelectedTab('stored-resourses')"
      :mode="storedResButtonMode"
      >Stored Resources</base-button
    >
    <base-button
      @click="setSelectedTab('add-resource')"
      :mode="addResButtonMode"
      >Add Resources</base-button
    >
  </base-card>
  <keep-alive>
  <component :is="selectedTab"></component>
  </keep-alive>
</template>
<script>
import StoredResourses from './StoredResourses.vue';
import AddResource from './AddResource.vue';
export default {
  components: { StoredResourses, AddResource },
  data() {
    return {
      setSelectedTab
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The official Vue.js documentation.',
          link: 'https://vuejs.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to google...',
          link: 'https://google.org',
        },
      ],
    };
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource:this.addResource,
    };
  },
  computed: {
    storedResButtonMode() {
      return this.selectedTab === 'stored-resourses' ? null : 'flat';
    },
    addResButtonMode() {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    },
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title,description,url){
      const newResourse={
        id:new Date().toISOString(),
        title:title,
        description:description,
        link:url,
      }
      this.storedResources.unshift(newResourse);
      this.selectedTab='stored-resourses'
    }
  },
};
</script>
