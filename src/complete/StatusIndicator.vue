<template>
  <span
    :aria-label="statusLabel"
    class="h-4 w-4 rounded-full flex items-center justify-center"
    :class="colorClasses.ring"
  >
    <span class="h-2 w-2 rounded-full" :class="colorClasses.dot"></span>
  </span>
</template>

<script>
export default {
  props: ['status'],
  setup(props) {
    return {
      statusLabel: {
        active: 'Active',
        inactive: 'Inactive',
      }[props.status],
      colorClasses: {
        active: {
          ring: 'bg-green-100',
          dot: 'bg-green-400',
        },
        inactive: {
          ring: 'bg-gray-100',
          dot: 'bg-gray-400',
        },
      }[props.status],
    }
  },
}
</script>