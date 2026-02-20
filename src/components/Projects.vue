<template>
    <section class="pb-5" id="projects">
        <h1 class="mt-5 mb-5 pb-4 text-center">My Projects</h1>
        <div
            v-for="(group, index) in chunkedProjects"
            :key="index"
            class="card-deck my-5 justify-content-center"
            >
            <ProjectCard
                v-for="project in group"
                :key="project.id"
                :project="project"
            />
        </div>
    </section>

    <!-- <section class="pb-5" id="projects">
        <h1 class="mt-5 mb-5 pb-4 text-center">My Projects</h1>

        <div class="row justify-content-center">
        <div 
            v-for="project in projects" 
            :key="project.id" 
            class="col-12 col-sm-6 col-md-4 mb-4"
        >
            <ProjectCard :project="project" />
        </div>
        </div>
    </section> -->

</template>


<script setup>
    // import computed for dynamic calculated state
    import {computed} from "vue";

    // import ProjectCard component
    import ProjectCard from "./ProjectCard.vue";

    // import projects data
    import projects from "../data/projects.json";

    // number of projects per row
    const chunkSize = 3;

    // compute projects in chunks of 3
    const chunkedProjects = computed(() => {
        const chunks = []; // array to store project groups
    
        for (let i = 0; i < projects.length; i+= chunkSize) {
            chunks.push(projects.slice(i, i + chunkSize)) // take 3 projects at a time
        } 
        return chunks // return grouped projects

    })
</script>