<template></template>

<script>
import BadgeCheckIcon from 'heroicons/vue/solid/BadgeCheck'
import CollectionIcon from 'heroicons/vue/solid/Collection'
import GitHubIcon from './GitHubIcon.vue'

export default {
  props: ['user'],
  components: {
    BadgeCheckIcon,
    CollectionIcon,
    GitHubIcon,
  },
  setup(props) {
    return {
      user: props.user,
    }
  },
}
</script>