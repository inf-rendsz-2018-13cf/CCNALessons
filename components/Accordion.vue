<template lang='pug'>
  section.accordions
    article.accordion(@click.prevent='collapse')
      .accordion-header.toggle
        p.tooltip.is-tooltip-multiline.is-tooltip-info(
          :data-tooltip='task.title.translated'
          v-text='`${task.id}. ${task.title.original}`'
        )
      .accordion-body
        .accordion-content
          ul
            //- TODO: id, correct
            li.tooltip.is-tooltip-info(
              v-for='(answer, key) in task.answers'
              :key='key'
              :class="{ 'has-text-primary': answer.description.correct, 'has-text-danger': !answer.description.correct }"
              v-text='answer.description.original'
              :data-tooltip='answer.description.translated'
            )
</template>

<script>
export default {
  props: {
    task: {
      required: true,
      type: Object
    }
  },
  methods: {
    collapse: ({ currentTarget }) =>
      currentTarget.classList.toggle('is-active')
  }
}
</script>

<style lang='sass' scoped>
  @import '~bulma'
  @import '../assets/styles/sass/accordion'
  @import '../assets/styles/sass/tooltip'
</style>
