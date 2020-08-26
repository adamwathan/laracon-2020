<template>
  <span class="inline-flex rounded-md shadow-sm">
    <button type="button" :class="[baseClasses, colorClasses]">
      <slot />
    </button>
  </span>
</template>

<script>
export default {
  props: {
    color: {
      validator(value) {
        return ['indigo', 'white'].includes(value)
      },
    },
  },
  setup(props) {
    const colorClasses = {
      indigo:
        'border-transparent text-white bg-indigo-600 hover:bg-indigo-500 focus:border-indigo-700 focus:shadow-outline-indigo active:bg-indigo-700',
      white:
        'border-gray-300 text-gray-700 bg-white hover:text-gray-500 focus:border-blue-300 focus:shadow-outline-blue active:text-gray-800 active:bg-gray-50',
    }
    return {
      baseClasses:
        'w-full inline-flex items-center justify-center px-4 py-2 border text-sm leading-5 font-medium rounded-md focus:outline-none transition ease-in-out duration-150',
      colorClasses: colorClasses[props.color],
    }
  },
}
</script>