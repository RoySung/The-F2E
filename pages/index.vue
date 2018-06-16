<template>
  <section class="container">
    <h1 class="title">
      The F2E
    </h1>
    <div class="links-list">
      <router-link to="/todolist">1. Todo List</router-link>
      <router-link to="/filter">1. Filter</router-link>
    </div>
  </section>
</template>

<script>
export default {
  components: {}
}
</script>

<style lang="sass">
.container
  min-height: 100vh
  display: flex
  justify-content: center
  align-items: center
  text-align: center
  flex-direction: column


.title
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif /* 1 */
  display: block
  font-weight: 300
  font-size: 100px
  color: #35495e
  letter-spacing: 1px


.subtitle
  font-weight: 300
  font-size: 42px
  color: #526488
  word-spacing: 5px
  padding-bottom: 15px


.links-list
  padding-top: 15px
  display: flex
  flex-direction: column
  a
    text-align: left


</style>
