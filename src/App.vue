<script>
import axios from 'axios';

import AppHeader from './components/AppHeader.vue';
import ProjectCard from './components/ProjectCard.vue';
const apiUri = 'http://localhost:8001/api/'
export default {
  name: 'App',
  components: {AppHeader, ProjectCard},
  data() { 
    return {
      projects: []
    }
  },
  methods: {
    fetchProjects(){
      axios.get(apiUri + 'projects').then(res => {
        
        this.projects = res.data;
        
      });
    }
  },
  created() {
    this.fetchProjects();
  }
}
</script>

<template>
<AppHeader></AppHeader>
<ProjectCard :projects="projects"></ProjectCard>   


</template>

<style lang="scss">
</style>