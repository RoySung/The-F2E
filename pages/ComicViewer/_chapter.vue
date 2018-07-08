<template>
  <div :class="{ 'dark-theme': isDarkTheme }" class="reading-page">
    <div class="selection-bar">
      <label class="selection-bar__name">My Hexschool<i class="fas fa-caret-right"></i></label>
      <select v-model="chatpterIndex" type="text" class="selection-bar__chapter-select">
        <option
          v-for="(chapter, index) in chatpersArr"
          :key="`chapter-${index}`"
          :value="index"
          v-html="chapter.name" />
      </select>
      <select v-model="currentPage" type="text" class="selection-bar__page-select">
        <option
          v-for="(img, index) in currentChapter.images"
          :key="`page-${img}`"
          :value="index"
          v-html="`Page ${index + 1}`" />
      </select>
      <div class="selection-bar__toggle-wrap">
        <i class="fas fa-sun"></i>
        <input v-model="isDarkTheme" type="checkbox" id="dark-theme-toggler" name="theme-toggler">
        <label for="dark-theme-toggler" class="input-slider"></label>
        <i v-if="isDarkTheme" class="fas fa-moon"></i>
        <i v-else class="far fa-moon"></i>
      </div>
    </div>
    <div class="content-wrap">
      <div class="main-slider-wrap">
        <div class="main-slider-wrap__nav-wrap">
          <button :disabled="currentPage <= 0" class="nav-btn nav-btn-prev" @click="prevmainSlick"><i class="fas fa-angle-left"></i></button>
          <button :disabled="currentPage >= currentChapter.images.length - 1" class="nav-btn nav-btn-next" @click="nextmainSlick"><i class="fas fa-angle-right"></i></button>
        </div>
        <slick
          ref="mainSlick"
          :options="mainSlickOptions"
          @beforeChange="handleMainSlickBeforeChange"
          >
          <img
            v-for="(imgSrc, index) in currentChapter.images"
            :key="`img-${index}-${imgSrc}`"
            :src="imgSrc"
            alt="">
        </slick>
      </div>
    </div>
  </div>
</template>

<script>
  // if(process.client) {
  //   const Slick = require('vue-slick')
  // }
  // import Slick from 'vue-slick

  export default {
    name: "Chapter",
    data() {
      return {
        isDarkTheme: false,
        chatpersArr: [
          {
            name: 'Chatper 1',
            images: [
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-1.png',
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-2.png',
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-3.png',
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-4.png',
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-5.png',
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-6.png',
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-7.png',
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-8.png',
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-9.png',
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-10.png',
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-11.png',
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-12.png',

            ]
          },
          {
            name: 'Chatper 2',
            images: [
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-2.png',
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-1.png',
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-3.png',
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-4.png',
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-5.png',
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-6.png',
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-7.png',
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-8.png',
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-9.png',
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-10.png',
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-11.png',
              'https://hexschool.github.io/THE_F2E_Design/week5-comic%20viewer/assets/storyboard-12.png',

            ]
          }
        ],
        mainSlickOptions: {
          slidesToShow: 1,
          arrows: false,
          infinite: false
        },
        currentPage: 0
      }
    },
    computed: {
      chatpterIndex: {
        get() {
          return this.$route.params.chapter
        },
        set(index) {
          let params = this.$route.params
          params.chapter = index
          this.$router.push({ params })
        }
      },
      currentChapter() {
        return this.chatpersArr[this.chatpterIndex]
      }
    },
    watch: {
      currentChapter() {
        this.$refs.mainSlick.destroy()
        this.$nextTick(() => {
          this.$refs.mainSlick.create()
          this.currentPage = 0
        })
      },
      currentPage(index) {
        this.$refs.mainSlick.goTo(index)
      }
    },
    methods: {
      prevmainSlick() {
        this.$refs.mainSlick.prev()
      },
      nextmainSlick() {
        this.$refs.mainSlick.next()
      },
      handleMainSlickBeforeChange(event, slick, currentSlide, nextSlide) {
        this.currentPage = nextSlide
      },
    },
    mounted() {
    },
    components: {
      // Slick
    }
  }
</script>

<style lang="sass" src="./chapter.sass" scoped>

</style>
