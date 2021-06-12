<template>
  <div class="justify-self-center mt-14 w-3/5">
    <div v-if="projects.length" class="space-y-4">
      <div v-for="project in projects" :key="project.id">
        <SingleProject :project="project"/>
      </div>  
    </div>
  </div>
</template>

<script>
import SingleProject from '../components/SingleProject.vue'

export default {
  name: 'Home',
  components: {
    SingleProject,
  },
  data() {
    return {
      projects: []
    }
  },
  mounted() {
    fetch('http://localhost:3000/projects')
    .then(res => res.json())
    .then(data => this.projects = data)
    .catch(err => console.log(err.message))
  }
}
</script>
