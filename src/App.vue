<template>
  <div class="bg-gradient-to-bl from-slate-50 to-slate-100 w-screen h-screen flex justify-center items-center">
  <div class="flex flex-col items-center sm:max-w-md w-full h-full sm:h-fit p-7 drop-shadow-2xl sm:rounded-[15px] bg-gradient-to-bl from-blue-500 to-indigo-700">
    <Header />
    <Searchbar @on-search="onSearch" />
    <MeaningSection :definition="currentDefinition" />
    <p v-show="noDefinition" class="text-center text-slate-300 text-xl mb-7">No definition found</p>
    <div class="absolute bottom-0 mb-2">
        <span>
          <img src="./assets/github.png" class="h-7 w-7 invert inline-block mr-3" />   
        </span>
        <span class="text-white">Built by : </span>
        <a href="https://github.com/isaacdigs" class="text-white underline">Isaac Digs</a>
    </div>
  </div>
 </div>
</template>

<script lang="ts">
import {defineComponent} from 'vue';
import Header from './components/Header.vue'
import Searchbar from './components/Searchbar.vue'
import MeaningSection from './components/MeaningSection.vue'

export default defineComponent({
  name: 'App',
  components: {
    Header,
    Searchbar,
    MeaningSection,
  },
  data(): any {
    return{
      currentDefinition: {
        word: '',
        phonetics: {
          text: '',
        },
        meanings: [
          {
            partOfSpeech: '',
            definitions: [
              {
                definition: '',
                example: '',
                synonyms: [],
                antonyms: [],
              }
            ]
          }
        ]
      },
      searchText: '',
      noDefinition: false,
    }
  },
  methods: {
    async getDefinition(word: string): Promise<any> {
      //return this.definitions.find((definition: { word: string; }) => definition.word === word);
      const response = await fetch(`https://api.dictionaryapi.dev/api/v2/entries/en/${word}`);
      const data = await response.json();
      return data[0];
    },
    onSearch(searchText: any) {
      this.searchText = searchText
      const queriedDefinition = this.getDefinition(this.searchText);
      queriedDefinition.then(
        (definition: any) => {
          const {word, phonetics, meanings } = definition;
          this.currentDefinition = {
            word,
            phonetics,
            meanings,
          },
          this.noDefinition = false;
        }
      ).catch(
        (error: any) => {
          console.log(error);
          this.noDefinition = true;
          this.currentDefinition = {
            word: '',
            phonetics: {},
            meanings: [],
          }
        }
      )
    },
  },
})

</script>
