<template>
  <nav class="justify-self-center mt-10 space-x-4 text-gray-400 font-semibold tracking-wider">
    <router-link :to="{ name: 'Home'}" class="inline-block hover:text-gray-500">Projects</router-link>
    <router-link :to="{ name: 'AddProject'}" class="inline-block hover:text-gray-500">Add a new Project</router-link>
  </nav>
</template>

<script>
export default {

}
</script>

<style>
a.router-link-active {
    border-bottom: 2px solid #00ce89;
    padding-bottom: 4px;
  }
</style>