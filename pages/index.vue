<template lang='pug'>
  section.container
    .columns.is-mobile.is-centered
      .column.is-three-quarters
        accordion(v-for='(task, key) in tasks' :key='key' :task='task')
</template>

<script>
import Accordion from '@/components/Accordion'

export default {
  components: {
    Accordion
  },
  async asyncData({ app }) {
    const { tasks } = await app.$axios.$get('tasks/tasks.json')

    return { tasks }
  }
}
</script>
