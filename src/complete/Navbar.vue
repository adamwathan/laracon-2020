<template>
  <nav class="flex-shrink-0 bg-indigo-700">
    <div class="max-w-7xl mx-auto px-2 sm:px-4 lg:px-8">
      <div class="relative flex items-center justify-between h-16">
        <!-- Logo section -->
        <div class="flex items-center px-2 lg:px-0 xl:w-64">
          <div class="flex-shrink-0">
            <img
              class="h-8 w-auto"
              src="https://tailwindui.com/img/logos/workflow-mark-on-brand.svg"
              alt="Workflow logo"
            />
          </div>
        </div>

        <!-- Search section -->
        <div class="flex-1 flex justify-center lg:justify-end">
          <div class="w-full px-2 lg:px-6">
            <label for="search" class="sr-only">Search projects</label>
            <div class="relative text-indigo-300 focus-within:text-gray-400">
              <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                <svg class="h-5 w-5" fill="currentColor" viewBox="0 0 20 20">
                  <path
                    fill-rule="evenodd"
                    d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z"
                    clip-rule="evenodd"
                  />
                </svg>
              </div>
              <input
                id="search"
                class="block w-full pl-10 pr-3 py-2 border border-transparent rounded-md leading-5 bg-indigo-400 bg-opacity-25 text-indigo-300 placeholder-indigo-300 focus:outline-none focus:bg-white focus:placeholder-gray-400 focus:text-gray-900 sm:text-sm transition duration-150 ease-in-out"
                placeholder="Search projects"
                type="search"
              />
            </div>
          </div>
        </div>
        <div class="flex lg:hidden">
          <!-- Mobile menu button -->
          <button
            @click="isMobileMenuOpen = !isMobileMenuOpen"
            class="inline-flex items-center justify-center p-2 rounded-md text-indigo-400 hover:text-white hover:bg-indigo-600 focus:outline-none focus:bg-indigo-600 focus:text-white transition duration-150 ease-in-out"
          >
            <svg class="block h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M4 6h16M4 12h8m-8 6h16"
              />
            </svg>
          </button>
        </div>
        <!-- Links section -->
        <div class="hidden lg:block lg:w-80">
          <div class="flex items-center justify-end">
            <div class="flex">
              <a
                v-for="[title, link] in primaryLinks"
                :href="link"
                class="px-3 py-2 rounded-md text-sm leading-5 font-medium text-indigo-200 hover:text-white focus:outline-none focus:text-white focus:bg-indigo-600 transition duration-150 ease-in-out"
              >
                {{ title }}
              </a>
            </div>
            <!-- Profile dropdown -->
            <div class="ml-4 relative flex-shrink-0">
              <div>
                <button
                  @click="isUserMenuOpen = !isUserMenuOpen"
                  class="flex text-sm rounded-full text-white focus:outline-none focus:shadow-solid transition duration-150 ease-in-out"
                  id="user-menu"
                  aria-label="User menu"
                  aria-haspopup="true"
                >
                  <img
                    class="h-8 w-8 rounded-full"
                    src="https://images.unsplash.com/photo-1517365830460-955ce3ccd263?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=256&h=256&q=80"
                    alt=""
                  />
                </button>
              </div>
              <!-- Profile dropdown panel -->
              <transition
                enter-active-class="transition ease-out duration-100"
                enter-from-class="transform opacity-0 scale-95"
                enter-to-class="transform opacity-100 scale-100"
                leave-active-class="transition ease-in duration-75"
                leave-from-class="transform opacity-100 scale-100"
                leave-to-class="transform opacity-0 scale-95"
              >
                <div
                  v-if="isUserMenuOpen"
                  class="origin-top-right absolute right-0 mt-2 w-48 rounded-md shadow-lg"
                >
                  <div
                    class="py-1 rounded-md bg-white shadow-xs"
                    role="menu"
                    aria-orientation="vertical"
                    aria-labelledby="user-menu"
                  >
                    <a
                      v-for="[title, link] in secondaryLinks"
                      :href="link"
                      class="block px-4 py-2 text-sm leading-5 text-gray-700 hover:bg-gray-100 focus:outline-none focus:bg-gray-100 transition duration-150 ease-in-out"
                      role="menuitem"
                    >
                      {{ title }}
                    </a>
                  </div>
                </div>
              </transition>
              <!-- /Profile dropdown panel -->
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="block lg:hidden">
      <MobileMenu
        v-if="isMobileMenuOpen"
        :primaryLinks="primaryLinks"
        :secondaryLinks="secondaryLinks"
      />
    </div>
  </nav>
</template>

<script>
import { ref } from 'vue'
import MobileMenu from './MobileMenu.vue'
import FlyoverMobileMenu from './FlyoverMobileMenu.vue'

export default {
  components: {
    MobileMenu,
    FlyoverMobileMenu,
  },
  setup() {
    const isUserMenuOpen = ref(false)
    const isMobileMenuOpen = ref(false)

    return {
      isMobileMenuOpen,
      isUserMenuOpen,
      primaryLinks: [
        ['Documentation', '#'],
        ['Support', '#'],
      ],
      secondaryLinks: [
        ['View profile', '#'],
        ['Settings', '#'],
        ['Log out', '#'],
      ],
    }
  },
}
</script>




<!-- <FlyoverMobileMenu
  :show="isMobileMenuOpen"
  @close="isMobileMenuOpen = false"
  :primaryLinks="primaryLinks"
  :secondaryLinks="secondaryLinks"
/> -->