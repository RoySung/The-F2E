<template>
  <ul class="list-wrap">
    <li
      v-for="(item, index) in listArrWithPage"
      :key="`item-${index}-${item.timeStamp}`"
      class="list-item"
    >
      <ul>
        <li class="item__link-wrap">
          <i class="fa fa-link" aria-hidden="true"></i>
          <a class="demo-link" target="black" :href="item.url" v-html="item.url"></a>
        </li>
        <li class="item__stage-wrap">
          <i class="fa fa-list-ol" aria-hidden="true"></i>
          <div class="stage-text" v-html="stages[item.stage - 1].name"></div>
        </li>
        <li class="item__date-wrap">
          <i class="fa fa-calendar" aria-hidden="true"></i>
          <div class="date-text" v-html="new Date(item.timeStamp).toLocaleString()"></div>
        </li>
        <li class="item__tags-wrap">
          <Tags title='<i class="fa fa-tags" aria-hidden="true"></i>' :options="item.tag.split(',').map(str => str.trim())"></Tags>
        </li>
      </ul>
    </li>
    <div class="pages-wrap">
      <button class="pages-btn prev-btn" @click="prevPage">
        <i class="fa fa-arrow-circle-left" aria-hidden="true"></i>
      </button>
      <span class="pages-text" v-html="`${page} / ${lastPage}`"></span>
      <button class="pages-btn next-btn" @click="nextPage">
        <i class="fa fa-arrow-circle-right" aria-hidden="true"></i>
      </button>
    </div>
  </ul>
</template>

<script>
  import Tags from '~/components/Tags'
  import { stages } from '~/constants/filter'
  export default {
    name: "FilterList",
    props: {
      listArr: Array
    },
    data() {
      return {
        stages,
        limitCount: 10
      }
    },
    computed: {
      page: {
        get() {
          let page = this.$route.query.page
          page = this.checkPage(page)
          return page
        },
        set(page) {
          let query = Object.assign({}, this.$route.query)
          page = this.checkPage(page)
          query.page = page
          this.$router.push({ query })
        }
      },
      lastPage() {
        return Math.ceil(this.listArr.length / this.limitCount)
      },
      listArrWithPage() {
        const { limitCount, page, listArr } = this
        const start = limitCount * (page - 1)
        const end = start +  limitCount
        return listArr.slice(start, end)
      }
    },
    methods: {
      checkPage(page) {
        return page = page > this.lastPage ? this.lastPage : page < 1 ? 1 : page
      },
      prevPage() {
        let page = this.page - 1
        page = page < 1 ? 1 : page
        this.page = page
      },
      nextPage() {
        let page = this.page + 1
        page = page > this.lastPage ? this.lastPage : page
        this.page = page
      }
    },
    mounted() {
      if (!this.page) this.page = 1
    },
    components: {
      Tags
    }
  }
</script>

<style lang="sass">
@import '~@/styles/mixins/breakpoints'

.list-wrap
  font-family: 'Teko', sans-serif
  color: #53588a
  padding: 0
  .list-item
    display: block
    background: #fff
    border-radius: 20px
    padding: 20px
    margin-top: 20px
    ul
      padding-left: 10px
    .item
      &__link-wrap,
      &__stage-wrap,
      &__date-wrap,
      &__tags-wrap
        display: flex
        font-size: 1.2rem
        i
          margin-right: 10px
      &__link-wrap
        overflow: auto
      &__tags-wrap
        h2
          font-size: 1.2rem
        .tags-wrap
          flex-direction: row
          .tags
            padding: 0
            .tag
              font-size: 1rem
              min-width: 50px
              padding: 0 5px

  .pages-wrap
    text-align: center
    font-size: 1.5rem
    .pages-btn
      border: unset
      background: transparent
      font-size: 1.3rem
      color: #53588a
      outline: unset
      cursor: pointer
    .pages-text

</style>
