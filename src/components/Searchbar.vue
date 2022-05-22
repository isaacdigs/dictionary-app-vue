<template>
    <form class="mt-1 flex flex-row">
        <input 
            type="text" 
            class="shadow-inner border focus:ring-indigo-500 focus:border-indigo-500 w-full pl-7 pr-12 border-gray-300 rounded mr-3 drop-shadow" 
            v-model="searchText"
        />
        <input type="submit" value="SEARCH" @click="onSearch" class="font-bold py-2 w-full flex justify-center items-center bg-blue-900 hover:bg-blue-800 hover:relative hover:bottom-[1px] hover:drop-shadow text-white rounded shadow-2xl">
    </form>
</template>

<script>
    export default {
        name: 'Searchbar',
        data() {
            return {
                searchText: '',
            }
        },
        methods: {
            onSearch(e) {
                e.preventDefault();
                this.$emit('on-search', this.searchText);
            },
        },
    }
</script>