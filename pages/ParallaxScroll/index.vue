<template>
  <div id="parallax-scroll-page">
    <section ref="openingSection" class="banner-section">
      <div ref="rect" class="rect"></div>
      <div ref="circle" class="circle"></div>
      <div ref="star" class="star">
        <div class="trapezoid trapezoid--top"></div>
        <div class="trapezoid trapezoid--bottom"></div>
      </div>
      <h1 class="banner-section__title">GEOMETRY PERSON</h1>
      <h3 class="banner-section__subtitle">find your core personality type in shapes!</h3>
    </section>
    <section ref="q1" class="question-section question-section__one">
      <div class="faq-wrap">
        <div class="q-wrap">
          <h1 class="q-wrap__number">Q1</h1>
          <h2 class="q-wrap__question">If one day you get a gift that can change the rule of the world, which ability will you choose?</h2>
          <h3 class="q-wrap__note">Choose the answer appeared in your mind instantly</h3>
        </div>
        <div class="a-wrap">
          <button class="option-btn">Destroy all humans in the world</button>
          <button class="option-btn">Make the war never happened</button>
          <button class="option-btn">You won’t get old and live forever</button>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
  import anime from 'animejs'

  export default {
    name: "ParallaxScroll",
    methods: {
      async opening() {
        const { rect, circle, star, openingSection } = this.$refs
        anime({
          targets: rect,
          rotate: [
            {
              value: "-1turn",
              easing: "easeInQuad",
              duration: 2000
            }
          ],
          scale: [{
            value: 7,
            delay: 2100,
            easing: "easeInQuad",
            duration: 1500
          }],
        })

        anime({
          targets: circle,
          scale: [
            {
              value: 1.2,
              easing: "easeInQuad",
              duration: 800
            },
            {
              value: 0.9,
              easing: "easeInQuad",
              duration: 500
            },
            {
              value: 1,
              easing: "easeOutQuad",
              duration: 700
            },
            {
              value: 7,
              easing: "easeInQuad",
              delay: 500,
              duration: 1300
            },
          ]
        })

        anime({
          targets: star,
          rotate: [
            {
              value: "1turn",
              easing: "easeInQuad",
              duration: 2000
            }
          ],
          scale: [
            {
              value: 7,
              easing: "easeInQuad",
              delay: 3000,
              duration: 300
            },
          ]
        })

        await anime({
          targets: openingSection,
          easing: "easeInQuad",
          opacity: 0,
          delay: 3300,
          duration: 500
        }).finished
      }
    },
    mounted() {
      setTimeout(async () => {
        await this.opening()

        anime({
          targets: this.$refs.q1,
          easing: "easeInQuad",
          opacity: 1,
          duration: 500,
        })
      }, 500)
    }
  }
</script>

<style lang="sass" src="./style.sass" scoped>

</style>
