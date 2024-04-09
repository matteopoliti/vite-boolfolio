<template>
    <main class="container">
        <div class="row"> 
                <ProjectCard v-for="(element, index) in arrayProjects" :key="element.id" :propsElement="element" />
        </div>

        <div class="pagination">
           
            <ul>
                <li>
                    <button @click="getProjects( currentPage - 1 )" :class="{'disabled': currentPage === 1}">
                        <i class="fa-solid fa-arrow-left"></i> Prev
                    </button>
                </li>

                <li v-for="(item, index) in lastPage" :key="index">
                    <button @click="getProjects( item )" :class="{'active': currentPage === item}">{{ item }}</button>
                </li>

                <li>
                    <button @click="getProjects( currentPage + 1 )" :class="{'disabled': currentPage === lastPage}">
                        Next <i class="fa-solid fa-arrow-right"></i>
                    </button>
                </li>
            </ul>
        </div>
    </main>
</template>

<script>
import axios from "axios";
import ProjectCard from "../components/Main/ProjectCard.vue";
export default {
    name: "ProjectList",
    components: {
        ProjectCard
    },
    data() {

        return {
            arrayProjects: [],
            currentPage: '',
            lastPage: ''
        }
    },
    methods: {
        getProjects( projectApiPage ) {
            axios.get('http://127.0.0.1:8000/api/projects',
                { 
                    params: {
                        page: projectApiPage
                    }
                })
                .then(res => {
                    // console.log(res.data.projects)

                    this.arrayProjects = res.data.projects.data
                    this.currentPage = res.data.projects.current_page
                    this.lastPage = res.data.projects.last_page
                })
        },
    },
    mounted() {
        this.getProjects( 1 )
    },
}
</script>

<style lang="scss" scoped>
.row {
    display: flex;
    justify-content: center;
    align-items: end;
    gap: 40px;
    flex-wrap: wrap;
}
.pagination{
    display: flex;
    justify-content: center;
    align-items: center;
    margin-block: 50px;
   
    ul{
        list-style-type: none;
        display: flex;
        background: rgba(255, 255, 255, 0.05);
        .disabled{
            pointer-events: none;
            background-color: black;
            color: #ccc;
        }
        .active{
            background: rgba(0, 0, 0, 0.5);
        }
        li{
            button{
                border: none;
                padding: 11px;
                padding: 20px 25px;
                color: #f9a300;
                font-weight: 500;
                font-size: 16px;
                cursor: pointer;
                &:hover{
                    background: rgba(0, 0, 0, 0.5);
                }
                i{
                    margin-inline: 5px;
                }
            }
        }
    }
    
}
</style>