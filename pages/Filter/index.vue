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
      <div v-if="isLoading" class="loading-wrap">
        <div class="loading-mask"></div>
        <div class="loading">
          <i class="fa fa-5x fa-spinner fa-pulse"></i>
        </div>
      </div>
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
        selectedTags: [],
        codeList: null,
        isLoading: false
      }
    },
    methods: {
      init() {
        this.isLoading = true
        fetch('https://www.thef2e.com/api/codeList')
          .then(res => res.json())
          .then(result => {
            this.codeList = result
            this.isLoading = false
          })
      },
      search() {
        this.isSearched = true
        this.init()
      }
    },
    mounted() {
    },
    components: {
      Tags
    }
  }
</script>

<style lang="sass" src="./style.sass">
</style>
