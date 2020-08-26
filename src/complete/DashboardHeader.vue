<template>
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
            <IconBadge :href="user.githubUrl">
              <GitHubIcon />
              <span>
                {{ user.username }}
              </span>
            </IconBadge>
          </div>
        </div>
        <!-- Action buttons -->
        <div
          class="flex flex-col space-y-3 space-x-0 sm:space-y-0 sm:space-x-3 sm:flex-row xl:flex xl:flex-col xl:space-y-3 xl:space-x-0"
        >
          <Button color="indigo">
            New Project
          </Button>
          <Button color="white">
            Invite Team
          </Button>
        </div>
      </div>
      <!-- Meta info -->
      <div
        class="flex flex-col space-y-6 space-x-0 sm:flex-row sm:space-y-0 sm:space-x-8 xl:flex xl:flex-col xl:space-y-6 xl:space-x-0"
      >
        <IconBadge>
          <BadgeCheckIcon />
          <span>Pro Member</span>
        </IconBadge>
        <IconBadge>
          <CollectionIcon />
          <span>{{ user.projectCount }} Projects</span>
        </IconBadge>
      </div>
    </div>
  </div>
</template>

<script>
import Button from './Button.vue'
import BadgeCheckIcon from 'heroicons/vue/solid/BadgeCheck'
import CollectionIcon from 'heroicons/vue/solid/Collection'
import GitHubIcon from './GitHubIcon.vue'
import IconBadge from './IconBadge.vue'

export default {
  props: ['user'],
  components: {
    Button,
    BadgeCheckIcon,
    CollectionIcon,
    GitHubIcon,
    IconBadge,
  },
  setup(props) {
    return {
      user: props.user,
    }
  },
}
</script>




<!--

layoutClasses({ stacked, horizontal }) {
  const classes = Object.entries(props.layout)
    .map(([screen, layout]) => {
      return (layout === 'stacked' ? stacked : horizontal)
        .split(' ')
        .map((c) => c.replace(/^\{screen\}:/, ''))
        .map((c) => (screen === 'default' ? c : `${screen}:${c}`))
        .join(' ')
    })
    .join(' ')

  return classes
},

-->