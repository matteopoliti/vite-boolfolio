<template>
    <main>
        <h1>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Vel aliquam blanditiis quam dolorum cumque earum
            illo, non inventore numquam, sint eveniet, nam sed quisquam neque odit? Maxime, qui minus. Deserunt!</h1>
    </main>
</template>

<script>
import axios from "axios";
export default {

    data() {

        return {

        }
    },
    methods: {
        getProjects() {
            axios.get('http://127.0.0.1:8000/api/projects')
                .then(res => {
                    console.log(res.data.projects)
                })
        }
    },
    mounted() {
        this.getProjects()
    },
}
</script>

<style lang="scss" scoped></style>