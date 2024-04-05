<template>
    <main class="container">
        <div class="row">
            <ProjectCard v-for="(element, index) in arrayProjects" :key="element.id" :propsElement="element" />

        </div>
    </main>
</template>

<script>
import axios from "axios";
import ProjectCard from "./ProjectCard.vue";
export default {
    components: {
        ProjectCard
    },
    data() {

        return {
            arrayProjects: []
        }
    },
    methods: {
        getProjects() {
            axios.get('http://127.0.0.1:8000/api/projects')
                .then(res => {
                    console.log(res.data.projects)

                    this.arrayProjects = res.data.projects
                })
        }
    },
    mounted() {
        this.getProjects()
    },
}
</script>

<style lang="scss" scoped>
.row {
    display: flex;
    align-items: end;
    gap: 20px;
    flex-wrap: wrap;
}
</style>