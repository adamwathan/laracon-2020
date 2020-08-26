<template>
  <div class="flex items-center">
    <div class="flex-1 whitespace-no-wrap">
      <slot name="heading" />
    </div>
    <div>
      <slot name="actions" />
    </div>
  </div>
</template>

<script>
export default {}
</script>
