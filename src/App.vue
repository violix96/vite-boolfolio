<script>
import axios from 'axios';

export default {
  name: 'Projects',
  data() {
    return {
      title: 'Projects',
      projects: [],
    };
  },
  methods: {
    getProjects() {
      const result = axios.get('http://127.0.0.1:8000/api/projects')
        .then(response => {
          console.log(response);

          if (response.data.status && response.data.results.length) {
            console.log('gestisco i risultati della risposta');
            console.log(response.data.results)

            this.projects = response.data.results

          } else {
            console.log('qualcosa è andato a buon fine');
          }

        }).catch(error => console.log(error));
      console.log(result)

    }
  },
  created() {
    this.getProjects();
  }
}
</script>

<template>
  <div class="container">
    <div class="row">
      <div class="col-12 text-center">
        <h1 class="mb-5">{{ title }}</h1>
      </div>
    </div>
    <div class="row">
      <div class="col-md-4 mb-4" v-for="(project, index) in projects" :key="project.id">
        <div class="card h-100">
          <div class="card-body">
            <h5 class="card-title">{{ project.title }}</h5>
            <p class="card-text">{{ project.description }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<style lang="scss" scoped></style>
