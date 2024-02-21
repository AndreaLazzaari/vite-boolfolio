<template lang="">
  <main class="container">
        <section class="row">
            <div class="col-12">
                <h1>
                    Our latest projects:
                </h1>
                <ul>

                    <li v-for="project in projects" :key="project.id">
                        {{ project.title }} -- {{ project.author }} -- {{ project.request }}
                    </li>
                </ul>

            </div>
        </section>
    </main>
</template>
<script>

import axios from 'axios';

export default {
    name: 'AppMain',
    data(){
        return{
            projects: [],
        }
    },
    methods:{
        getProjects(){
            axios.get('http://127.0.0.1:8000/api/projects', {
                params: {
                }
            })
            .then((response) => {
                console.log(response.data.results.data);
                this.projects = response.data.results.data;
            })
            .catch(function (error) {
                console.warn(error);
            })
        }
    },
    created(){
        this.getProjects();
    }
}
</script>
<style lang="">
    
</style>