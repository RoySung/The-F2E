<template>
  <div class="card list-wrap transaction-website">
    <h4 class="list-wrap__title">Transaction Website</h4>
    <ul class="list-wrap__list transaction-website__list">
      <li
        v-for="item in list"
        :key="item.url"
        class="list-wrap__item transaction-website__item">
        <div class="transaction-website__item__img">
          <i :class="getIconClass(item.platform)"></i>
        </div>
        <div class="transaction-website__item__name" v-html="item.url"></div>
        <div class="transaction-website__item__count" v-html="item.total.toLocaleString()"></div>
        <div :class="{ green: item.trend == 'up', red: item.trend == 'down' }" class="transaction-website__item__percent">
          <i v-if="item.trend == 'up'" class="fas fa-arrow-up"></i>
          <i v-if="item.trend == 'down'" class="fas fa-arrow-down"></i>
          <span v-html="`${item.percent}%`"></span>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: "TransactionWebsite",
    props: {
      list: Array
    },
    mounted() {
      console.log(this.list)
    },
    methods: {
      getIconClass(platform) {
        switch (platform) {
          case 'Wordpress':
            return 'fab fa-wordpress'
          case 'Shopify':
            return 'fas fa-shopping-bag'
          case 'Google':
            return 'fab fa-google'
          case 'Facebook':
            return 'fab fa-facebook'
        }
      }
    }
  }
</script>

<style lang="sass" src="./transactionWebsite.sass" scoped>

</style>
