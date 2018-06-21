<template>
  <div class="admin-page">
    <div class="header">
      <div class="header__logo-wrap">
        <h3 class="logo-text">Shop Admin</h3>
      </div>
      <div class="header__navigation-bar">
        <div class="navigation-tabs">
          <div class="tab">Home</div>
          <div class="tab">Orders</div>
          <div class="tab">Product</div>
        </div>
      </div>
      <div class="header__user-wrap">Admin</div>
    </div>
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
      <div class="card transaction-website">transaction</div>
      <div class="card latest-orders">orders</div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'AdminPage',
  }
</script>

<style lang="sass" src="./style.sass">
</style>
