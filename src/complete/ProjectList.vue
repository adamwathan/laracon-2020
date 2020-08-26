<template>
  <div>
    <div
      class="pl-4 pr-6 pt-4 pb-4 border-b border-t border-gray-200 sm:pl-6 lg:pl-8 xl:pl-6 xl:pt-6 xl:border-t-0"
    >
      <SectionHeading>
        <template #heading>
          <h1 class="text-lg leading-7 font-medium">Recent Projects</h1>
        </template>
        <template #actions>
          <div class="flex relative space-x-3">
            <Button color="white">
              Filters
            </Button>
            <Button color="white">
              <svg class="-ml-1 mr-2 h-5 w-5 text-gray-400" viewBox="0 0 20 20" fill="currentColor">
                <path
                  d="M3 3a1 1 0 000 2h11a1 1 0 100-2H3zM3 7a1 1 0 000 2h5a1 1 0 000-2H3zM3 11a1 1 0 100 2h4a1 1 0 100-2H3zM13 16a1 1 0 102 0v-5.586l1.293 1.293a1 1 0 001.414-1.414l-3-3a1 1 0 00-1.414 0l-3 3a1 1 0 101.414 1.414L13 10.414V16z"
                />
              </svg>
              Sort
            </Button>
          </div>
        </template>
      </SectionHeading>
    </div>
    <ul class="relative z-0 divide-y divide-gray-200 border-b border-gray-200">
      <li v-for="project in projects" class="">
        <div
          class="relative flex items-center justify-between space-x-4 hover:bg-gray-50 pl-4 pr-6 py-5 sm:py-6 sm:pl-6 lg:pl-8 xl:pl-6"
        >
          <!-- Repo name and link -->
          <div class="min-w-0 space-y-3">
            <div class="flex items-center space-x-3">
              <StatusIndicator :status="project.active ? 'active' : 'inactive'" />
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
              <IconBadge :href="project.repoUrl">
                <GitHubIcon />
                <span>
                  {{ project.repo }}
                </span>
              </IconBadge>
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
              <StarButton :active="project.starred" />
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
</template>

<script>
import Button from './Button.vue'
import GitHubIcon from './GitHubIcon.vue'
import StarButton from './StarButton.vue'
import StatusIndicator from './StatusIndicator.vue'
import IconBadge from './IconBadge.vue'
import SectionHeading from './SectionHeading.vue'

export default {
  components: {
    Button,
    GitHubIcon,
    StarButton,
    StatusIndicator,
    IconBadge,
    SectionHeading,
  },
  props: ['projects'],
}
</script>