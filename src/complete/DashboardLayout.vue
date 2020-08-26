<template>
  <div>
    <!-- Background color split screen for large screens -->
    <div class="fixed top-0 left-0 w-1/2 h-full bg-white"></div>
    <div class="fixed top-0 right-0 w-1/2 h-full bg-gray-50"></div>

    <div class="relative min-h-screen flex flex-col">
      <slot name="header" />

      <!-- 3 column wrapper -->
      <div class="flex-grow w-full max-w-7xl mx-auto lg:flex">
        <!-- Left sidebar & main wrapper -->
        <div class="flex-1 min-w-0 bg-white xl:flex xl:pl-8">
          <div class="xl:flex-shrink-0 xl:w-64 xl:border-r xl:border-gray-200 bg-white">
            <div class="pl-4 pr-6 py-6 sm:pl-6 lg:pl-8 xl:pl-0">
              <slot name="leftColumn" />
            </div>
          </div>
          <div class="bg-white lg:min-w-0 lg:flex-1">
            <slot name="centerColumn" />
          </div>
        </div>
        <div
          class="bg-gray-50 pr-4 sm:pr-6 lg:pr-8 lg:flex-shrink-0 lg:border-l lg:border-gray-200"
        >
          <div class="pt-6 pl-6 lg:w-80">
            <slot name="rightColumn" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: [],
  components: {},
  setup() {
    //...
  },
}
</script>