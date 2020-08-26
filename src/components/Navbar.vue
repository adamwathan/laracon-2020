<template></template>

<script>
import { ref } from 'vue'
export default {
  components: {
    // ...
  },
  setup() {
    const isUserMenuOpen = ref(false)
    const isMobileMenuOpen = ref(false)

    return {
      isMobileMenuOpen,
      isUserMenuOpen,
    }
  },
}
</script>