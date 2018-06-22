<template>
  <div class="card list-wrap transaction-website">
    <h4 class="list-wrap__title">Transaction Website</h4>
    <ul class="list-wrap__list transaction-website__list">
      <li class="list-wrap__item transaction-website__item">
        <div class="transaction-website__item__img">
          <i class="fab fa-facebook"></i>
        </div>
        <div class="transaction-website__item__name">Facebook.com</div>
        <div class="transaction-website__item__count">45,836</div>
        <div class="transaction-website__item__percent green">
          <i class="fas fa-arrow-up"></i>
          20%
        </div>
      </li>
      <li class="list-wrap__item transaction-website__item">
        <div class="transaction-website__item__img">
          <i class="fab fa-google"></i>
        </div>
        <div class="transaction-website__item__name">google.com</div>
        <div class="transaction-website__item__count">23,582</div>
        <div class="transaction-website__item__percent green">
          <i class="fas fa-arrow-up"></i>
          12%
        </div>
      </li>
      <li class="list-wrap__item transaction-website__item">
        <div class="transaction-website__item__img">
          <i class="fas fa-shopping-bag"></i>
        </div>
        <div class="transaction-website__item__name">Shopify.com</div>
        <div class="transaction-website__item__count">2,489</div>
        <div class="transaction-website__item__percent red">
          <i class="fas fa-arrow-down"></i>
          15%
        </div>
      </li>
      <li class="list-wrap__item transaction-website__item">
        <div class="transaction-website__item__img">
          <i class="fab fa-wordpress"></i>
        </div>
        <div class="transaction-website__item__name">Wordpress.com</div>
        <div class="transaction-website__item__count">1,057</div>
        <div class="transaction-website__item__percent red">
          <i class="fas fa-arrow-down"></i>
          30%
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: "TransactionWebsite"
  }
</script>

<style lang="sass" src="./transactionWebsite.sass" scoped>

</style>
