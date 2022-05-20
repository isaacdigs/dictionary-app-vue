<template>
  <div class="bg-gradient-to-bl from-slate-50 to-slate-100 w-screen h-screen flex justify-center items-center">
  <div class="p-7 drop-shadow-2xl rounded bg-gradient-to-bl from-blue-500 to-indigo-700">
    <Header />
    <Searchbar @on-search="onSearch" />
    <MeaningSection :definition="currentDefinition" />
    <p class="text-white text-center">* Hard-coded: cat, dog, elephant</p>
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
      definitions: [
        {
          word: 'cat',
          phonetics: {
            text: 'kæt',
          },
          meanings: [
            {
              partOfSpeech: 'noun',
              definitions: [
                {
                  definition: 'a small domesticated carnivorous mammal with soft fur, a short snout, and retractile claws.',
                  example: 'I love cats',
                  synonyms: [],
                  antonyms: [],
                }
              ]
            },
            {
              partOfSpeech: 'verb',
              definitions: [
                {
                  definition: 'to be in a state of complete bliss',
                  example: 'I am happy',
                  synonyms: [],
                  antonyms: [],
                }
              ]
            }
          ],
        },
        {
          word: 'dog',
          phonetics: {
            text: 'dɒg',
          },
          meanings: [
            {
              partOfSpeech: 'noun',
              definitions: [
                {
                  definition: 'a domesticated carnivorous mammal that typically has a long snout, an acute sense of smell, and a barking, howling, or whining voice.',
                  example: 'I love dogs',
                  synonyms: [],
                  antonyms: [],
                }
              ]
            },
            {
              partOfSpeech: 'verb',
              definitions: [
                {
                  definition: 'to be in a state of complete bliss',
                  example: 'I am happy',
                  synonyms: [],
                  antonyms: [],
                }
              ]
            }
          ],
        },
        {
          word: 'elephant',
          phonetics: {
            text: 'ɪlˈfɑːnt',
          },
          meanings: [
            {
              partOfSpeech: 'noun',
              definitions: [
                {
                  definition: 'a large, long-necked mammal with a trunk and trunk-like trunk',
                  example: 'I love elephants',
                  synonyms: [],
                  antonyms: [],
                }
              ]
            },
            {
              partOfSpeech: 'verb',
              definitions: [
                {
                  definition: 'to be in a state of complete bliss',
                  example: 'I am happy',
                  synonyms: [],
                  antonyms: [],
                }
              ]
            }
          ],
        },
      ],
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
    }
  },
  methods: {
    getDefinition(word: string): any {
      return this.definitions.find((definition: { word: string; }) => definition.word === word);
    },
    displayDefinition(definition: Object) {
      this.currentDefinition = definition
    },
    onSearch(searchText) {
      this.searchText = searchText
      this.currentDefinition = this.getDefinition(this.searchText)
    },
  },
})

</script>
