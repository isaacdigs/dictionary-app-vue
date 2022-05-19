<script lang="ts">
import Header from './components/Header.vue'
import Searchbar from './components/Searchbar.vue'
import MeaningSection from './components/MeaningSection.vue'

export default {
  name: 'App',
  components: {
    Header,
    Searchbar,
    MeaningSection,
  }
}
</script>

<template>
  <div class="bg-gradient-to-bl from-slate-50 to-slate-100 w-screen h-screen flex justify-center items-center">
  <div class="p-7 drop-shadow-2xl rounded bg-gradient-to-bl from-blue-500 to-indigo-700">
    <Header />
    <Searchbar />
    <MeaningSection />
  </div>
 </div>
</template>

<style>
  /* body {
    display: flex;
    height: 100vh;
    width: 100vw;
    justify-content: center;
    align-items: center;
  } */
</style>