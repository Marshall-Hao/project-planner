<template>
    <div  class="bg-gray-100 px-5 py-5 space-y-4 rounded-sm shadow-sm border-l-4 border-red-500" :class="{ 'border-green-500' : project.complete }">
        <div class="font-bold text-gray-600 text-md flex justify-between">
            <div @click="showDetails = !showDetails">{{ project.title }}</div>
            <div class="flex space-x-3 cursor-pointer">
                <span class="material-icons text-sm text-gray-400 hover:text-gray-600">
                    edit
                </span>
                <span @click="deleteProject" class="material-icons text-sm text-gray-400 hover:text-gray-600">
                    delete
                </span>
                <span @click="toggleComplete" class="material-icons text-sm text-gray-400 hover:text-gray-600" :class="{ 'text-green-500' : project.complete }">
                    done
                </span>
            </div>
        </div>
        <div v-if="showDetails"   class="font-medium text-gray-400 text-xs">
            {{ project.details }}
        </div>
    </div>
</template>

<script>
export default {
    props: ['project'],
    data() {
        return {
            showDetails: false,
            url: `http://localhost:3000/projects/${this.project.id}`
        }
    },
    methods: {
        deleteProject() {
            fetch(this.url, { method: 'DELETE'})
            .then(() => this.$emit('delete', this.project.id))
            .catch(err => console.log(err.message))
        },
        toggleComplete() {
            fetch(this.url, { 
            method: 'PATCH',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify({ complete: !this.project.complete })
            }).then(() => {
                this.$emit('complete', this.project.id)
            }).catch(err => console.log(err.message))
        }
    },
}
</script>

<style>

</style>