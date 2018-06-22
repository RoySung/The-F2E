<template>
  <div class="admin-page">
    <Header />

    <div class="overview-wrap">
      <h3 class="title-wrap">Overview</h3>
      <div class="filter-wrap">filter</div>
      <div class="card total-view total-revenue-wrap">
        <h4 class="total-view__title"><i class="fas fa-hand-holding-usd"></i>TOTAL REVENUE</h4>
        <div class="total-view__count">54,540</div>
      </div>
      <div class="card total-view total-cost-wrap">
        <h4 class="total-view__title"><i class="fas fa-money-check-alt"></i>TOTAL COST</h4>
        <div class="total-view__count">12,660</div>
      </div>
      <div class="card total-view net-income-wrap">
        <h4 class="total-view__title"><i class="fas fa-money-bill"></i>NET INCOME</h4>
        <div class="total-view__count">41,880</div>
      </div>

      <div class="card analytics-chart">chart</div>

      <TransactionWebsite />

      <div class="card latest-orders">orders</div>
    </div>
  </div>
</template>

<script>
  import Header from './Header'
  import TransactionWebsite from './TransactionWebsite'
  export default {
    name: 'AdminPage',
    components: {
      Header,
      TransactionWebsite
    }
  }
</script>

<style lang="sass" src="./index.sass">
</style>
