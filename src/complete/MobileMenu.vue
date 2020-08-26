<template>
  <div>
    <div class="px-2 pt-2 pb-3 space-y-1">
      <a
        v-for="[title, link] in primaryLinks"
        :href="link"
        class="block px-3 py-2 rounded-md text-base font-medium text-indigo-200 hover:text-indigo-100 hover:bg-indigo-600 focus:outline-none focus:text-white focus:bg-indigo-600 transition duration-150 ease-in-out"
      >
        {{ title }}
      </a>
    </div>
    <div class="pt-4 pb-3 border-t border-indigo-800">
      <div class="px-2 space-y-1">
        <a
          v-for="[title, link] in secondaryLinks"
          :href="link"
          class="block px-3 py-2 rounded-md text-base font-medium text-indigo-200 hover:text-indigo-100 hover:bg-indigo-600 focus:outline-none focus:text-white focus:bg-indigo-600 transition duration-150 ease-in-out"
        >
          {{ title }}
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['primaryLinks', 'secondaryLinks'],
}
</script>