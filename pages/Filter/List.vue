<template>
  <ul class="list-wrap">
    <li
      v-for="(item, index) in listArr"
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
      }
    },
    computed: {
      page: {
        get() {
          return this.$route.query.page
        },
        set(page) {
          let query = Object.assign({}, this.$route.query)
          query.page = page
          this.$router.push({ query })
        }
      }
    },
    mounted() {
      this.page = 1
    },
    components: {
      Tags
    }
  }
</script>

<style lang="sass">
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
    .item
      &__link-wrap,
      &__stage-wrap,
      &__date-wrap,
      &__tags-wrap
        display: flex
        font-size: 1.2rem
        i
          margin-right: 10px
      &__tags-wrap
        h2
          font-size: 1.2rem
        .tag
          font-size: 1rem
          min-width: 50px
          padding: 0 5px

</style>
