<script>
export default {
    props: {projects: Array}, 
    
}
</script>


<template>

<div class="container mt-5">

    <h1 class="text-center fw-bold text-primary my-5">
        My projects
    </h1>

    <div class="row g-3">
        <div v-for="project in projects" class="col-4">
            <div class="card text-center">
                <img :src="project.image" class="card-img-top" alt="...">
                <div class="card-body">
                    <h5 class="card-title">{{ project.title }}</h5>
                    <p class="card-text">{{ `${project.description.slice(0, 85)}...` }}</p>
                    <!-- <a :href="project.project.link" class="btn btn-primary">View the project</a> -->
                    <div class="buttons">
                        <a :href="project.project_link" class="btn btn-primary me-2">GitHub link</a>
                        <router-link class="btn btn-success" :to="{name: 'project-details', params: {id: project.id}}">Details</router-link>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>  

</template>


<style scoped lang="scss">
    .card {
        img {
            height: 250px;
        }
    }
</style>