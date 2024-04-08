<template>
    <figure>
            <img :src="'http://127.0.0.1:8000/storage/' + project.cover_image" alt="">
    </figure>
    <div class="info">
        <h3>{{ project.title }}</h3>
        <p><strong>Description:</strong> {{ project.description }}</p>
        <span v-if="project.type"><strong>Type:</strong> {{ project.type.type }}</span>
        <p v-if="project.technologies != ''">
            <strong>Technologies:</strong>
            <span v-for="(item, index) in project.technologies" :key="item.id">
                {{ item.name + ', ' }}
            </span>
        </p>

    </div>
</template>

<script>
import axios from "axios";
export default {
    name: 'SingleProject',
    data () {


        return {
            project: [],
        }
    },
    methods: {
        getSingleProject(){
            axios.get(`http://127.0.0.1:8000/api/projects/${this.$route.params.slug}`)
            .then( res=>{
                if(res.data.success){
                    this.project = res.data.project
                    // console.log(res.data.project)
                }else{

                }
            })
        }
    },
    mounted() {
        this.getSingleProject()
    },
}
</script>

<style lang="scss" scoped>
figure {

    img {
        width: 500px;
    }
}

.info {
    padding: 20px;
    min-height: 200px;
    h3 {
        color: #f9a300;
        text-transform: uppercase;
        font-size: 30px;
        font-weight: bold;
    }

    p {
        text-transform: capitalize;
        font-size: 24px;
        letter-spacing: 1px;
        margin-block: 20px;
    }

    span {
        text-transform: capitalize;
        font-size: 24px;
        letter-spacing: 1px;
        margin-block: 10px;
    }
}
</style>