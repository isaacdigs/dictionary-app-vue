<script lang="ts">
    export default {
        name: 'MeaningSection',
        props: {
            definition: Object,
        }
    }
</script>

<template>
    <div class="scrollbar p-3 bg-slate-50 my-5 shadow-inner overflow-y-scroll sm:h-[240px] min-h-[150px] w-full border">
        <span class="font-extrabold text-indigo-900 text-2xl">{{definition.word}}</span>
        <span class="text-gray-400 text-sm ml-2">{{definition.phonetics.text}}</span>
        <audio />
        <i></i> <!--audio icon-->
        <div :key="meaning"  v-for="(meaning, index) in definition.meanings">
            <span>{{definition.word.length !== 0 ? index + 1 + '.' : ''}}</span>
            <span class="ml-2 text-indigo-500">{{meaning.partOfSpeech}}</span>
            <p>{{meaning.definitions[0].definition}}</p>
            <p class="text-slate-400 italic">{{meaning.definitions[0].example ?'"' + meaning.definitions[0].example + '"': ''}}</p>
            <br />
        </div>
    </div>
</template>

<style scoped>
.scrollbar::-webkit-scrollbar {
    width: 20px;
    height: 20px;
}

.scrollbar::-webkit-scrollbar-track {
    border-radius: 100vh;
    background: #edf0f7;
}

.scrollbar::-webkit-scrollbar-thumb {
    background: rgb(49 46 129);
    border-radius: 100vh;
    border: 3px solid #f6f7ed;
}

.scrollbar::-webkit-scrollbar-thumb:hover {
    background: rgb(30 58 138);
}


</style>