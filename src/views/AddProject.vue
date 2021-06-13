<template>
  <form @submit.prevent="handleSubmit" class="justify-self-center grid space-y-4 bg-white p-5 rounded-lg w-3/5 mt-10 shadow-lg">
      <label class="block text-gray-400 font-bold text-sm tracking-wider">Title:</label>
      <input class="block w-full border-b border-gray-300 focus:outline-none text-gray-300 font-medium text-sm" type="text" v-model="title" required>
      <label class="block text-gray-400 font-bold text-sm tracking-wider">Details:</label>
      <textarea class="block w-full border-gray-300 border focus:outline-none text-gray-300 font-medium text-sm rounded-md h-20"  v-model="details" required></textarea>
      <button class="block justify-self-center px-4 py-3 bg-green-500 text-gray-50 font-semibold rounded-xl shadow-md focus:outline-none bg-opacity-90 hover:bg-opacity-100">Add Project</button>
  </form>
</template>

<script>
export default {
    data() {
        return {
            title: '',
            details: ''
        }
    },
    methods: {
        handleSubmit() {
           let project = {
               title: this.title,
               details: this.details,
               complete: false
            }
            
            fetch('http://localhost:3000/projects', {
                method: 'POST',
                headers: {'Content-Type': 'application/json'},
                body: JSON.stringify(project)
            }).then(() => {
                this.$router.push('/')
            }).catch(err => console.log(err.message))
        }
    }
}
</script>

<style>

</style>