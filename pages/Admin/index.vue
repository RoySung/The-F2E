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
      <Orders :orders="latestOrders" />
    </div>
  </div>
</template>

<script>
  import Header from './Header'
  import TransactionWebsite from './TransactionWebsite'
  import Orders from './Orders'
  export default {
    name: 'AdminPage',
    data() {
      return {
        latestOrders: [
          {
            title: 'Vintage T-shirt',
            imgSrc: 'https://pixabay.com/get/e837b20b2efc063ecd0b4606e248459ee66ae3d01bb8194491f2c47c.jpg',
            time: '2018/6/13  13:42',
            customer: 'Belle Willis',
            price: 3200
          },
          {
            title: 'Cowboy Jacket',
            imgSrc: 'https://pixabay.com/get/e837b20b2efc063ecd0b4606e248459ee66ae3d01bb8194491f2c47c.jpg',
            time: '2018/6/13  10:45',
            customer: 'Adrian Cummings',
            price: 2800
          },
          {
            title: 'Coach Coat',
            imgSrc: 'https://pixabay.com/get/e837b20b2efc063ecd0b4606e248459ee66ae3d01bb8194491f2c47c.jpg',
            time: '2018/6/13  8:26',
            customer: 'Lura Holland',
            price: 1600
          }
        ]
      }
    },
    components: {
      Header,
      TransactionWebsite,
      Orders
    }
  }
</script>

<style lang="sass" src="./index.sass">
</style>
