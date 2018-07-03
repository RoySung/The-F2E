<template>
  <div class="comic-viewer-page">
    <div class="header header--bright">
      <h1 class="header-title">Comicomic</h1>
    </div>
    <div class="info-wrap">
      <div class="info-wrap__image">
        <img src="@/static/comic/comic_cover.png" alt="">
      </div>
      <div class="info-wrap__content">
        <div class="info-wrap__content__title">
          <h2>MY HEXSCHOOL</h2>
        </div>
        <ul class="info-wrap__content__info">
          <li class="info-genres"><span>Genres</span>Fusce/vehicula/dolor</li>
          <li class="info-author"><span>Author</span>Namae Shiranai</li>
          <li class="info-status"><span>Status</span>Ongoing</li>
          <li class="info-rate"><span>Rate</span></li>
          <li class="info-summary">
            <span>Summary</span>
            <p>If your banker breaks, you snap; if your apothecary by mistake sends you poison in your pills, you die.<br><br>Therefore, I say, I saw that this situation of mine was the precise situation of every mortal that has this Siamese connexion with a plurality of other mortals. </p>
          </li>
        </ul>
      </div>
    </div>
    <div class="chapters-wrap">
      <div class="chapters-wrap__title">
        <h3>All Chapters</h3>
      </div>
      <div class="chapters-wrap__content">
        <p>Chapter 1: The F2E Challenge Start!</p>
        <p>Chapter 2: Todo List is Going Crazy! <span class="new-tag">New</span></p>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "ComicViewer"
  }
</script>

<style lang="sass" src="./style.sass" scoped>
</style>
