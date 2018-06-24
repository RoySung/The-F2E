<template>
  <div class="card latest-orders">
    <h4 class="list-wrap__title">Latest Orders</h4>
    <ul class="list-wrap__list orders__list">
      <li
        v-for="order in orders"
        :key="order.time"
        class="list-wrap__item orders__item">
        <div class="orders__item__img" :style="{ 'background-image': `url(${order.imgSrc})` }">
        </div>
        <div class="orders__item__info">
          <p class="info-title" v-html="order.title"></p>
          <p class="info-time">
            <i class="fas fa-clock"></i>
            <span v-html="order.time"></span>
          </p>
          <p class="info-customer">
            <i class="fas fa-male"></i>
            <span v-html="order.customer"></span>
          </p>
        </div>
        <div class="orders__item__count">
          <p class="count-prefix">Total</p>
          <p class="count-number" v-html="order.price"></p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: 'Orders',
    props: {
      orders: Array
    }
  }
</script>

<style lang="sass" src="./orders.sass" scoped>

</style>
