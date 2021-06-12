<template>
    <div @click="showDetails = !showDetails" class="bg-gray-100 px-5 py-5 space-y-4 rounded-sm shadow-sm border-l-4 border-red-500">
        <div class="font-bold text-gray-600 text-md flex justify-between">
            {{ project.title }}
            <div class="flex space-x-3 cursor-pointer">
                <span class="material-icons text-sm text-gray-400 hover:text-gray-600">
                    edit
                </span>
                <span class="material-icons text-sm text-gray-400 hover:text-gray-600">
                    delete
                </span>
                <span class="material-icons text-sm text-gray-400 hover:text-gray-600">
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
            showDetails: false
        }
    }
}
</script>

<style>

</style>