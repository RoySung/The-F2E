<template>
  <div :class="{ 'dark-theme': isDarkTheme }" class="reading-page">
    <div class="selection-bar">
      <label class="selection-bar__name">My Hexschool<i class="fas fa-caret-right"></i></label>
      <select type="text" class="selection-bar__chapter-select">
        <option value="1">Chapter 1</option>
        <option value="2">Chapter 2</option>
      </select>
      <select type="text" class="selection-bar__page-select">
        <option value="1">Chapter 1</option>
        <option value="2">Chapter 2</option>
      </select>
      <div class="selection-bar__toggle-wrap">
        <i class="fas fa-sun"></i>
        <input v-model="isDarkTheme" type="checkbox" id="dark-theme-toggler" name="theme-toggler">
        <label for="dark-theme-toggler" class="input-slider"></label>
        <i v-if="isDarkTheme" class="fas fa-moon"></i>
        <i v-else class="far fa-moon"></i>
      </div>

    </div>

    {{ $route.params.chapter }}

  </div>
</template>

<script>
  export default {
    name: "Chapter",
    data() {
      return {
        isDarkTheme: false,
        chatpersArr: [
          {
            name: 'Chatper 1',
            content: [
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
          }
        ],
        chatpterIndex: 0
      }
    },
    computed: {
    }
  }
</script>

<style lang="sass" src="./chapter.sass" scoped>

</style>
