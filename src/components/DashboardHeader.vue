<template></template>

<script>
import Button from './Button.vue'
import BadgeCheckIcon from 'heroicons/vue/solid/BadgeCheck'
import CollectionIcon from 'heroicons/vue/solid/Collection'
import GitHubIcon from './GitHubIcon.vue'

export default {
  props: ['user'],
  components: {
    Button,
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