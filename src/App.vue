<script>
import axios from 'axios';

import AppHeader from './components/AppHeader.vue';
import ProjectCard from './components/ProjectCard.vue';
import AppLoader from './components/AppLoader.vue';
const apiUri = 'http://localhost:8001/api/'
export default {
  name: 'App',
  components: {AppHeader, ProjectCard, AppLoader},
  data() { 
    return {
      projects: [],
      isLoading: false
    }
  },
  methods: {
    fetchProjects(){
      this.isLoading = true;
      axios.get(apiUri + 'projects').then(res => {
        
        this.projects = res.data;

        }).catch(err => {
          console.log(err);
          
        }).then(() => {
          this.isLoading = false;
          
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
<AppLoader v-if="isLoading"/>
    <h1 v-else-if="!projects.length" class="text-center">No projects found!</h1> 


</template>

<style lang="scss">
</style>