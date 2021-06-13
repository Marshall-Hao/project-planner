<template>
  <nav class="space-x-5 mb-4">
    <button @click="updateFilter('all')" class="inline-block text-sm text-gray-400 font-semibold focus:outline-none hover:text-gray-500" :class="{ 'text-gray-500': current === 'all'}">
        View All
    </button>
     <button @click="updateFilter('completed')" class="inline-block text-sm text-gray-400 font-semibold focus:outline-none hover:text-gray-500" :class="{ 'text-gray-500': current === 'completed'}">
        Completed
    </button>
     <button @click="updateFilter('ongoing')" class="inline-block text-sm text-gray-400 font-semibold focus:outline-none hover:text-gray-500" :class="{ 'text-gray-500': current === 'ongoing'}">
        Ongoing
    </button>
  </nav>
</template>

<script>
export default {
    props: ['current'],
    methods: {
        updateFilter(by) {
            this.$emit('filterChange', by)
        }
    }
}
</script>

<style>

</style>