<template>
  <div class="tags-wrap">
    <h2 v-html="title"></h2>
    <ul class="tags">
      <li
        class="tag"
        :class="{ 'tag--active': value && value.includes(option), 'tag--disabled': !value }"
        v-for="(option, index) in optionsWithObject"
        :key="`option-${option.value}`"
        v-html="option.name"
        @click="value && selectTag(index)"
      >
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: "Tags",
    props: {
      title: String,
      options: Array,
      value: Array
    },
    computed: {
      optionsWithObject() {
        return this.options.map(option => {
          if (Object.keys(option).includes('name') && Object.keys(option).includes('value')) {
            return option
          } else {
            return {
              name: option,
              value: option
            }
          }
        })
      }
    },
    methods: {
      selectTag(optionIndex) {
        const { options, value } = this
        let arr = [...value]
        let index = arr.indexOf(options[optionIndex])
        if (index != -1) {
          arr.splice(index, 1)
        } else {
          arr.push(options[optionIndex])
        }
        this.$emit('input', arr)
      }
    }
  }
</script>

<style lang="sass" scoped>
.tags-wrap
  display: flex
  flex-direction: column
  font-family: 'Teko', sans-serif
  color: #53588a
  .tags
    display: flex
    flex-wrap: wrap
    font-size: 1.2rem
    padding: 0 10px
    .tag
      display: block
      min-width: 100px
      float: left
      padding: 5px 10px
      text-align: center
      margin: 5px
      cursor: pointer
      border-radius: 20px
      border: 0.12em solid #53588a
      color: #616373
      text-transform: capitalize
      color: #53588a
      &--active
        color: #fff
        background: #53588a
      &--disabled
        cursor: unset

</style>
