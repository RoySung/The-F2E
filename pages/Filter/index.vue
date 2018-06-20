<template>
  <div class="filter-page">
    <div :class="{ 'search-wrap--searched': isSearched }" class="search-wrap">
      <h1 class="search-title">The F2E</h1>
      <div class="search-input-wrap">
        <input class="search-input" type="text" v-model="searchInputText" @keyup.enter="search" autofocus>
        <i class="fas fa-search" @click="search"></i>
      </div>
      <div id="search-btn" @click="search">Search</div>
    </div>
    <transition name="fade">
      <div v-if="isSearched" class="content">
        <div v-if="isLoading" class="loading-wrap">
          <div class="loading-mask"></div>
          <div class="loading">
            <i class="fa fa-5x fa-spinner fa-pulse"></i>
          </div>
        </div>
        <Tags class="stages-wrap" isToggler="true" title="Stages" :options="stages" v-model="selectedStage"></Tags>
        <Tags class="tags-wrap" isToggler="true" title="Tags" :options="tags" v-model="selectedTags"></Tags>
        <h3 v-if="filtedResult" class="result-count" v-html="resultCountText" ></h3>
        <List v-if="filtedResult" :listArr="filtedResult"></List>
      </div>
    </transition>
  </div>
</template>

<script>
  import fetch from 'node-fetch'
  import Tags from '~/components/Tags'
  import List from './List'
  import { stages, tags } from '~/constants/filter'

  export default {
    name: 'Filter',
    data() {
      return {
        searchInputText: null,
        isSearched: false,
        stages,
        tags,
        selectedStage: [stages[0]],
        selectedTags: [],
        codeList: null,
        isLoading: false
      }
    },
    watch: {
      selectedStage: {
        handler(arr) {
          this.isLoading = true
          Promise.all(arr.map(option => this.fetchDataWithStage(option.value))).then(resultArr => {
            const result = resultArr.reduce((acc, curr) => [...acc, ...curr], [])
            this.codeList = result
            this.isLoading = false
          })
        },
        immediate: true
      }
    },
    computed: {
      searchText: {
        get() {
          return this.$route.query.search
        },
        set(text) {
          console.log(text)
          let query = Object.assign({}, this.$route.query)
          query.search = text
          this.$router.push({ query })
        }
      },
      filtedResult() {
        const { selectedTags, codeList, searchText } = this
        if (!codeList) return codeList

        return codeList.filter(item => {
          const isTaged = selectedTags.length ? !selectedTags.some(tagOption => !item.tag.includes(tagOption.value)) : true
          const isSearched = searchText ? item.url.toLowerCase().includes(searchText) || item.tag.toLowerCase().includes(searchText) : true
          return isTaged && isSearched
        })
      },
      resultCountText() {
        return `${this.filtedResult.length} Results With Filter ...`
      }
    },
    methods: {
      fetchDataWithStage(stage) {
        return new Promise((resolve, reject) => {
          fetch(`https://www.thef2e.com/api/codeList?stage=${stage}`)
            .then(res => res.json())
            .then(result => {
              resolve(result)
            })
        })
      },
      search() {
        this.isSearched = true
        this.searchText = this.searchInputText
      }
    },
    mounted() {
      this.searchInputText = this.searchText
    },
    components: {
      Tags,
      List
    }
  }
</script>

<style lang="sass" src="./style.sass">
</style>
