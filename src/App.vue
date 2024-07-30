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
    <header>header</header>

    <main>
      <h1>{{ title }}</h1>
    </main>

    <footer>footer</footer>
  </div>
</template>

<style lang="scss" scoped></style>
