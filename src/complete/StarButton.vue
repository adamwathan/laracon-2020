<template>
  <button
    type="button"
    :class="[
      'inline-flex h-5 w-5',
      active ? 'text-yellow-300 hover:text-yellow-400' : 'text-gray-300 hover:text-gray-400',
    ]"
  >
    <StarIcon class="h-full w-full" />
  </button>
</template>

<script>
import StarIcon from 'heroicons/vue/solid/Star'

export default {
  props: ['active'],
  components: {
    StarIcon,
  },
  setup(props) {
    return {}
  },
}
</script>