<template>
  <div>
    <!-- Background color split screen for large screens -->
    <div class="fixed top-0 left-0 w-1/2 h-full bg-white"></div>
    <div class="fixed top-0 right-0 w-1/2 h-full bg-gray-50"></div>

    <div class="relative min-h-screen flex flex-col">
      <!-- Navbar -->
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
                    href="#"
                    class="px-3 py-2 rounded-md text-sm leading-5 font-medium text-indigo-200 hover:text-white focus:outline-none focus:text-white focus:bg-indigo-600 transition duration-150 ease-in-out"
                    >Documentation</a
                  >
                  <a
                    href="#"
                    class="px-3 py-2 rounded-md text-sm leading-5 font-medium text-indigo-200 hover:text-white focus:outline-none focus:text-white focus:bg-indigo-600 transition duration-150 ease-in-out"
                    >Support</a
                  >
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
                      v-show="isUserMenuOpen"
                      class="origin-top-right absolute right-0 mt-2 w-48 rounded-md shadow-lg"
                    >
                      <div
                        class="py-1 rounded-md bg-white shadow-xs"
                        role="menu"
                        aria-orientation="vertical"
                        aria-labelledby="user-menu"
                      >
                        <a
                          href="#"
                          class="block px-4 py-2 text-sm leading-5 text-gray-700 hover:bg-gray-100 focus:outline-none focus:bg-gray-100 transition duration-150 ease-in-out"
                          role="menuitem"
                          >View Profile</a
                        >
                        <a
                          href="#"
                          class="block px-4 py-2 text-sm leading-5 text-gray-700 hover:bg-gray-100 focus:outline-none focus:bg-gray-100 transition duration-150 ease-in-out"
                          role="menuitem"
                          >Settings</a
                        >
                        <a
                          href="#"
                          class="block px-4 py-2 text-sm leading-5 text-gray-700 hover:bg-gray-100 focus:outline-none focus:bg-gray-100 transition duration-150 ease-in-out"
                          role="menuitem"
                          >Sign out</a
                        >
                      </div>
                    </div>
                  </transition>
                  <!-- /Profile dropdown panel -->
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Mobile menu -->
        <div v-if="isMobileMenuOpen" class="lg:hidden">
          <div class="px-2 pt-2 pb-3 space-y-1">
            <a
              href="#"
              class="block px-3 py-2 rounded-md text-base font-medium text-indigo-200 hover:text-indigo-100 hover:bg-indigo-600 focus:outline-none focus:text-white focus:bg-indigo-600 transition duration-150 ease-in-out"
            >
              Documentation
            </a>
            <a
              href="#"
              class="block px-3 py-2 rounded-md text-base font-medium text-indigo-200 hover:text-indigo-100 hover:bg-indigo-600 focus:outline-none focus:text-white focus:bg-indigo-600 transition duration-150 ease-in-out"
            >
              Support
            </a>
          </div>
          <div class="pt-4 pb-3 border-t border-indigo-800">
            <div class="px-2 space-y-1">
              <a
                href="#"
                class="block px-3 py-2 rounded-md text-base font-medium text-indigo-200 hover:text-indigo-100 hover:bg-indigo-600 focus:outline-none focus:text-white focus:bg-indigo-600 transition duration-150 ease-in-out"
              >
                Your Profile
              </a>
              <a
                href="#"
                class="block px-3 py-2 rounded-md text-base font-medium text-indigo-200 hover:text-indigo-100 hover:bg-indigo-600 focus:outline-none focus:text-white focus:bg-indigo-600 transition duration-150 ease-in-out"
              >
                Settings
              </a>
              <a
                href="#"
                class="block px-3 py-2 rounded-md text-base font-medium text-indigo-200 hover:text-indigo-100 hover:bg-indigo-600 focus:outline-none focus:text-white focus:bg-indigo-600 transition duration-150 ease-in-out"
              >
                Sign out
              </a>
            </div>
          </div>
        </div>
        <!-- Mobile menu -->
      </nav>
      <!-- /Navbar -->

      <!-- 3 column wrapper -->
      <div class="flex-grow w-full max-w-7xl mx-auto lg:flex">
        <!-- Left sidebar & main wrapper -->
        <div class="flex-1 min-w-0 bg-white xl:flex xl:pl-8">
          <div class="xl:flex-shrink-0 xl:w-64 xl:border-r xl:border-gray-200 bg-white">
            <div class="pl-4 pr-6 py-6 sm:pl-6 lg:pl-8 xl:pl-0">
              <!-- Dashboard header -->
              <div class="flex items-center justify-between">
                <div class="flex-1 space-y-8">
                  <div
                    class="block space-y-8 sm:space-y-0 sm:flex sm:justify-between sm:items-center xl:block xl:space-x-0 xl:space-y-8"
                  >
                    <!-- Profile -->
                    <div class="flex items-center space-x-3">
                      <div class="flex-shrink-0 h-12 w-12">
                        <img class="h-12 w-12 rounded-full" :src="user.avatar" alt="" />
                      </div>
                      <div class="space-y-1">
                        <div class="text-sm leading-5 font-medium text-gray-900">
                          {{ user.name }}
                        </div>
                        <a :href="user.githubUrl" class="group flex items-center space-x-2">
                          <GitHubIcon class="h-5 w-5 text-gray-400 group-hover:text-gray-500" />
                          <span
                            class="text-sm text-gray-500 leading-5 font-medium group-hover:text-gray-900"
                          >
                            {{ user.username }}
                          </span>
                        </a>
                      </div>
                    </div>
                    <!-- Action buttons -->
                    <div
                      class="flex flex-col space-y-3 space-x-0 sm:space-y-0 sm:space-x-3 sm:flex-row xl:flex xl:flex-col xl:space-y-3 xl:space-x-0"
                    >
                      <span class="inline-flex rounded-md shadow-sm">
                        <button
                          type="button"
                          class="w-full inline-flex items-center justify-center px-4 py-2 border text-sm leading-5 font-medium rounded-md focus:outline-none transition ease-in-out duration-150 border-transparent text-white bg-indigo-600 hover:bg-indigo-500 focus:border-indigo-700 focus:shadow-outline-indigo active:bg-indigo-700"
                        >
                          New Project
                        </button>
                      </span>
                      <span class="inline-flex rounded-md shadow-sm">
                        <button
                          type="button"
                          class="w-full inline-flex items-center justify-center px-4 py-2 border text-sm leading-5 font-medium rounded-md focus:outline-none transition ease-in-out duration-150 border-gray-300 text-gray-700 bg-white hover:text-gray-500 focus:border-blue-300 focus:shadow-outline-blue active:text-gray-800 active:bg-gray-50"
                        >
                          Invite Team
                        </button>
                      </span>
                    </div>
                  </div>
                  <!-- Meta info -->
                  <div
                    class="flex flex-col space-y-6 space-x-0 sm:flex-row sm:space-y-0 sm:space-x-8 xl:flex xl:flex-col xl:space-y-6 xl:space-x-0"
                  >
                    <span class="flex items-center space-x-2">
                      <BadgeCheckIcon class="h-5 w-5 text-gray-400" />
                      <span class="text-sm text-gray-500 leading-5 font-medium">
                        Pro Member
                      </span>
                    </span>
                    <span class="flex items-center space-x-2">
                      <CollectionIcon class="h-5 w-5 text-gray-400" />
                      <span class="text-sm text-gray-500 leading-5 font-medium">
                        {{ user.projectCount }} Projects
                      </span>
                    </span>
                  </div>
                </div>
              </div>
              <!-- /Dashboard header -->
            </div>
          </div>
          <div class="bg-white lg:min-w-0 lg:flex-1">
            <!-- Project list -->
            <div>
              <div
                class="pl-4 pr-6 pt-4 pb-4 border-b border-t border-gray-200 sm:pl-6 lg:pl-8 xl:pl-6 xl:pt-6 xl:border-t-0"
              >
                <div class="flex items-center">
                  <h1 class="flex-1 text-lg leading-7 font-medium">Recent Projects</h1>
                  <div class="flex relative space-x-3">
                    <span class="rounded-md shadow-sm">
                      <button
                        type="button"
                        class="inline-flex justify-center w-full rounded-md border border-gray-300 px-4 py-2 bg-white text-sm leading-5 font-medium text-gray-700 hover:text-gray-500 focus:outline-none focus:border-blue-300 focus:shadow-outline-blue active:bg-gray-50 active:text-gray-800 transition ease-in-out duration-150"
                      >
                        Filters
                      </button>
                    </span>
                    <span class="rounded-md shadow-sm">
                      <button
                        type="button"
                        class="inline-flex justify-center w-full rounded-md border border-gray-300 px-4 py-2 bg-white text-sm leading-5 font-medium text-gray-700 hover:text-gray-500 focus:outline-none focus:border-blue-300 focus:shadow-outline-blue active:bg-gray-50 active:text-gray-800 transition ease-in-out duration-150"
                      >
                        <svg
                          class="-ml-1 mr-2 h-5 w-5 text-gray-400"
                          viewBox="0 0 20 20"
                          fill="currentColor"
                        >
                          <path
                            d="M3 3a1 1 0 000 2h11a1 1 0 100-2H3zM3 7a1 1 0 000 2h5a1 1 0 000-2H3zM3 11a1 1 0 100 2h4a1 1 0 100-2H3zM13 16a1 1 0 102 0v-5.586l1.293 1.293a1 1 0 001.414-1.414l-3-3a1 1 0 00-1.414 0l-3 3a1 1 0 101.414 1.414L13 10.414V16z"
                          />
                        </svg>
                        Sort
                      </button>
                    </span>
                  </div>
                </div>
              </div>
              <ul class="relative z-0 divide-y divide-gray-200 border-b border-gray-200">
                <li v-for="project in projects" class="">
                  <div
                    class="relative flex items-center justify-between space-x-4 hover:bg-gray-50 pl-4 pr-6 py-5 sm:py-6 sm:pl-6 lg:pl-8 xl:pl-6"
                  >
                    <!-- Repo name and link -->
                    <div class="min-w-0 space-y-3">
                      <div class="flex items-center space-x-3">
                        <span
                          :aria-label="project.active ? 'Active' : 'Inactive'"
                          class="h-4 w-4 rounded-full flex items-center justify-center"
                          :class="project.active ? 'bg-green-100' : 'bg-gray-100'"
                        >
                          <span
                            class="h-2 w-2 rounded-full"
                            :class="project.active ? 'bg-green-400' : 'bg-gray-400'"
                          ></span>
                        </span>

                        <span class="block">
                          <h2 class="text-sm font-medium leading-5">
                            <a href="#">
                              <span class="absolute inset-0"></span>
                              {{ project.name }}
                            </a>
                          </h2>
                        </span>
                      </div>
                      <div class="relative">
                        <a :href="project.repoUrl" class="group flex items-center space-x-2">
                          <GitHubIcon class="h-5 w-5 text-gray-400 group-hover:text-gray-500" />
                          <span
                            class="text-sm text-gray-500 leading-5 font-medium group-hover:text-gray-900"
                          >
                            {{ project.repo }}
                          </span>
                        </a>
                      </div>
                    </div>
                    <div class="sm:hidden">
                      <svg class="h-5 w-5 text-gray-400" viewBox="0 0 20 20" fill="currentColor">
                        <path
                          fill-rule="evenodd"
                          d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z"
                          clip-rule="evenodd"
                        />
                      </svg>
                    </div>
                    <!-- Repo meta info -->
                    <div class="hidden sm:flex flex-col flex-shrink-0 items-end space-y-3">
                      <p class="relative flex items-center space-x-4">
                        <a
                          :href="project.url"
                          class="relative text-sm leading-5 text-gray-500 hover:text-gray-900 font-medium"
                        >
                          Visit site
                        </a>
                        <button
                          type="button"
                          :class="[
                            'inline-flex h-5 w-5',
                            project.starred
                              ? 'text-yellow-300 hover:text-yellow-400'
                              : 'text-gray-300 hover:text-gray-400',
                          ]"
                        >
                          <StarIcon class="h-full w-full" />
                        </button>
                      </p>
                      <p class="flex text-gray-500 text-sm leading-5 space-x-2">
                        <span>{{ project.tech }}</span>
                        <span>&middot;</span>
                        <span>Last deploy {{ project.lastDeploy }}</span>
                        <span>&middot;</span>
                        <span>{{ project.location }}</span>
                      </p>
                    </div>
                  </div>
                </li>
              </ul>
            </div>
            <!-- /Project list -->
          </div>
        </div>
        <div
          class="bg-gray-50 pr-4 sm:pr-6 lg:pr-8 lg:flex-shrink-0 lg:border-l lg:border-gray-200"
        >
          <div class="pt-6 pl-6 lg:w-80">
            <!-- Activity feed -->
            <div>
              <div class="pb-2">
                <h2 class="text-sm leading-5 font-semibold">Activity</h2>
              </div>
              <div>
                <ul class="divide-y divide-gray-200">
                  <li v-for="item in activityItems" class="py-4">
                    <div class="flex space-x-3">
                      <img
                        class="h-6 w-6 rounded-full"
                        src="https://images.unsplash.com/photo-1517365830460-955ce3ccd263?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=256&h=256&q=80"
                        alt=""
                      />
                      <div class="flex-1 space-y-1">
                        <div class="flex items-center justify-between">
                          <h3 class="text-sm font-medium leading-5">You</h3>
                          <p class="text-sm leading-5 text-gray-500">{{ item.time }}</p>
                        </div>
                        <p class="text-sm leading-5 text-gray-500">
                          Deployed {{ item.project }} ({{ item.commit }} in master) to
                          {{ item.environment }}
                        </p>
                      </div>
                    </div>
                  </li>
                </ul>
                <div class="py-4 text-sm leading-5 border-t border-gray-200">
                  <a href="#" class="text-indigo-600 font-semibold hover:text-indigo-900">
                    View all activity &rarr;
                  </a>
                </div>
              </div>
            </div>
            <!-- /Activity feed -->
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'
import BadgeCheckIcon from 'heroicons/vue/solid/BadgeCheck'
import CollectionIcon from 'heroicons/vue/solid/Collection'
import StarIcon from 'heroicons/vue/solid/Star'
import GitHubIcon from './GitHubIcon.vue'

export default {
  components: {
    BadgeCheckIcon,
    CollectionIcon,
    StarIcon,
    GitHubIcon,
  },
  setup(props) {
    const isUserMenuOpen = ref(false)
    const isMobileMenuOpen = ref(false)

    return {
      isUserMenuOpen,
      isMobileMenuOpen,
      user: {
        name: 'Debbie Lewis',
        username: 'debbielewis',
        avatar:
          'https://images.unsplash.com/photo-1517365830460-955ce3ccd263?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=256&h=256&q=80',
        projectCount: 9,
        membership: 'Pro',
        githubUrl: 'https://example.com/debbielewis',
      },
      projects: [
        {
          name: 'Workcation',
          repo: 'debbielewis/workcation',
          repoUrl: 'https://example.com/debbielewis/workcation',
          url: '#',
          tech: 'Laravel',
          lastDeploy: '3h ago',
          location: 'United States',
          starred: true,
          active: true,
        },
        {
          name: 'EasyWire',
          repo: 'debbielewis/easywire',
          repoUrl: 'https://example.com/debbielewis/easywire',
          url: '#',
          tech: 'NextJS',
          lastDeploy: '6h ago',
          location: 'United States',
          starred: true,
          active: true,
        },
        {
          name: 'Workflow',
          repo: 'debbielewis/workflow',
          repoUrl: 'https://example.com/debbielewis/workflow',
          url: '#',
          tech: 'Laravel',
          lastDeploy: '4d ago',
          location: 'United States',
          starred: true,
          active: true,
        },
        {
          name: 'KiteTail',
          repo: 'debbielewis/kitetail',
          repoUrl: 'https://example.com/debbielewis/kitetail',
          url: '#',
          tech: 'Laravel',
          lastDeploy: '4d ago',
          location: 'United States',
          starred: false,
          active: false,
        },
        {
          name: 'Talk Slides',
          repo: 'debbielewis/talk-slides',
          repoUrl: 'https://example.com/debbielewis/talk-slides',
          url: '#',
          tech: 'Laravel',
          lastDeploy: '3h ago',
          location: 'United States',
          starred: true,
          active: true,
        },
        {
          name: 'Personal Website',
          repo: 'debbielewis/personal-website',
          repoUrl: 'https://example.com/debbielewis/personal-website',
          url: '#',
          tech: 'NextJS',
          lastDeploy: '6h ago',
          location: 'United States',
          starred: false,
          active: true,
        },
        {
          name: 'Digest',
          repo: 'debbielewis/digest',
          repoUrl: 'https://example.com/debbielewis/digest',
          url: '#',
          tech: 'Laravel',
          lastDeploy: '3h ago',
          location: 'United States',
          starred: false,
          active: false,
        },
        {
          name: 'Resumaid',
          repo: 'debbielewis/resumaid',
          repoUrl: 'https://example.com/debbielewis/resumaid',
          url: '#',
          tech: 'Laravel',
          lastDeploy: '3h ago',
          location: 'United States',
          starred: false,
          active: true,
        },
        {
          name: 'SponsorShip',
          repo: 'debbielewis/sponsorship',
          repoUrl: 'https://example.com/debbielewis/sponsorship',
          url: '#',
          tech: 'Laravel',
          lastDeploy: '3h ago',
          location: 'United States',
          starred: false,
          active: false,
        },
      ],
      activityItems: [
        {
          project: 'Workcation',
          commit: '2d89f0c8',
          environment: 'production',
          time: '1h',
        },
        {
          project: 'KiteTail',
          commit: '249df660',
          environment: 'staging',
          time: '3h',
        },
        {
          project: 'Workcation',
          commit: '11464223',
          environment: 'staging',
          time: '12h',
        },
        {
          project: 'Easywire',
          commit: 'dad28e95',
          environment: 'production',
          time: '2d',
        },
        {
          project: 'Easywire',
          commit: '624bc94c',
          environment: 'production',
          time: '5d',
        },
        {
          project: 'Workcation',
          commit: 'e111f80e',
          environment: 'production',
          time: '1w',
        },
        {
          project: 'Resumaid',
          commit: '5e136005',
          environment: 'staging',
          time: '1w',
        },
        {
          project: 'KiteTail',
          commit: '5c1fd07f',
          environment: 'production',
          time: '2w',
        },
      ],
    }
  },
}
</script>