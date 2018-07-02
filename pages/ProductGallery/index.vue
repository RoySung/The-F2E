<template>
  <div class="product-gallery">
    <div class="scroll-reveal banner-wrap"></div>
    <div class="scroll-reveal content-wrap">
      <h2 class="content-wrap__title">VINTAGE DENIM</h2>
      <h3 class="content-wrap__subtitle">Kogi Cosby sweater ethical squid irony</h3>
      <div class="content-wrap__content">
        <p>In the tumultuous business of cutting-in and attending to a whale, there is much running backwards and forwards among the crew. Now hands are wanted here, and then again hands are wanted there. There is no staying in any one place; for at one and the same time everything has to be done everywhere. It is much the same with him who endeavors the description of the scene.</p>
        <br>
        <p>We must now retrace our way a little. It was mentioned that upon first breaking ground in the whale's back, the blubber-hook was inserted into the original hole there cut by the spades of the mates. But how did so clumsy and weighty a mass as that same hook get fixed in that hole? It was inserted there by my particular friend Queequeg, whose duty it was, as harpooneer.</p>
      </div>
    </div>

    <div class="decorate-rect__first"></div>
    <div class="decorate-rect__second"></div>
    <div class="decorate-rect__third"></div>
    <div class="decorate-rect__fourth"></div>
    <div class="decorate-rect__fifth strip-bg"></div>

    <div class="scroll-reveal decorate-words__banner__top__right"><h2>VINTAGE</h2></div>
    <div class="scroll-reveal decorate-words__banner__right__top"><h2>DENIM</h2></div>
    <div class="scroll-reveal decorate-words__banner__bottom__left"><h2>TOP</h2></div>
    <div class="scroll-reveal decorate-words__banner__left__bottom"><h2>06</h2></div>

    <div class="scroll-reveal decorate-words__content"><h3>PRODUCT DETAILS</h3></div>
    <div class="scroll-reveal img-wrap__second"></div>
    <div class="scroll-reveal img-wrap__first"></div>
  </div>
</template>

<script>
  // import ScrollReveal from 'scrollreveal'
  export default {
    name: "ProductGallery",
    mounted() {
      this.$nextTick(() => {
        const ScrollReveal = require('scrollreveal')
        const sr = ScrollReveal({ reset: true })
        sr.reveal('.scroll-reveal', { duration: 800 }, 100)
      })
    }
  }
</script>

<style lang="sass" src="./style.sass" scoped>

</style>
