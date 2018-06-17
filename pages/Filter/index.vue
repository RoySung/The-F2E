<template>
  <div class="filter-page">
    <div :class="{ 'search-wrap--searched': isSearched }" class="search-wrap">
      <h1 class="search-title">The F2E</h1>
      <div class="search-input-wrap">
        <input class="search-input" type="text" v-moel="searchText" @keyup.enter="search">
        <i class="fas fa-search" @click="search"></i>
      </div>
      <div id="search-btn" @click="search">Search</div>
    </div>
    <div v-if="isSearched" class="content">
      <Tags class="stages-wrap" title="Stages" :options="stages" v-model="selectedStage"></Tags>
      <Tags class="tags-wrap" title="Tags" :options="tags" v-model="selectedTags"></Tags>
    </div>

  </div>
</template>

<script>
  import Tags from './Tags'
  import { stages, tags } from './constants'

  export default {
    name: 'Filter',
    data() {
      return {
        searchText: null,
        isSearched: false,
        stages,
        tags,
        selectedStage: [],
        selectedTags: []
      }
    },
    methods: {
      search() {
        console.log('search')
        this.isSearched = true
      }
    },
    components: {
      Tags
    }
  }
</script>

<style lang="sass" src="./style.sass">
</style>
