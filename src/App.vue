<script>
import axios from 'axios';

import AppHeader from './components/AppHeader.vue';
const apiUri = 'http://localhost:8001/api/'
export default {
  name: 'App',
  components: {AppHeader},
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


</template>

<style lang="scss">
</style>