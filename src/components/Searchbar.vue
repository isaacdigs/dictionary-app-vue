<template>
    <div class="mt-1 flex flex-row">
        <input 
            type="text" 
            name="search" 
            id="search" 
            class="border focus:ring-indigo-500 focus:border-indigo-500 w-full pl-7 pr-12 border-gray-300 rounded mr-3 drop-shadow" 
        />
        <a href="#" class="py-2 w-full flex justify-center items-center bg-indigo-900 hover:bg-blue-900 text-white rounded shadow-2xl">
            SEARCH
        </a>
    </div>
</template>

<script lang="ts">
    export default {
        name: 'Searchbar',
    }
</script>