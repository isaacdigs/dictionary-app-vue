<script lang="ts">
    export default {
        name: 'MeaningSection',
        props: {
            definition: Object,
        }
    }
</script>

<template>
    <div class="p-3 bg-slate-50 mt-5 shadow-inner h-64 w-full border">
        <span class="font-extrabold text-indigo-900 text-2xl">{{definition.word}}</span>
        <span class="text-gray-400 text-sm ml-2">{{definition.phonetics.text}}</span>
        <audio />
        <i></i> <!--audio icon-->
        <div v-for="(meaning, index) in definition.meanings">
            <span>{{definition.word.length !== 0 ? index + 1 + '.' : ''}}</span>
            <span class="ml-2 text-indigo-500">{{meaning.partOfSpeech}}</span>
            <p>{{meaning.definitions[0].definition}}</p>
            <p class="text-slate-400 italic">{{definition.word.length !==0?'"' + meaning.definitions[0].example + '"': ''}}</p>
            <br />
        </div>
    </div>
</template>