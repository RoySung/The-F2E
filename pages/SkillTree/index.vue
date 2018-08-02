<template>
  <div id="skill-tree-page">
    <section class="main-wrap">
      <h1 class="main-wrap__title">FRONT-END SKILL TREE</h1>

      <div class="rank-wrap">
        <div class="rank-wrap__label">CURRENT RANK</div>
        <div class="rank-wrap__name">FRONT-END NOOB</div>
      </div>

      <img src="@/static/skilltree/img-ship-noob.png" alt="" class="main-wrap__rocket-img">
      <div class="main-wrap__tips-text">
        Welcome aboard. Your mission is: Collect the resources and learn the skills to upgrade the ship. Good luck, captain!
      </div>

    </section>
    <section class="steps-wrap"></section>
    <section class="info-wrap"></section>
  </div>
</template>

<script>
  export default {
    name: "SkillTree"
  }
</script>

<style lang="sass" src="./style.sass" scoped>

</style>
