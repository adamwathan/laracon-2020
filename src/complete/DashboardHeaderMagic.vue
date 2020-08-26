<template>
  <div class="flex items-center justify-between">
    <div class="flex-1 space-y-8">
      <div
        :class="
          layoutClasses({
            stacked: '{screen}:block {screen}:space-y-8 {screen}:space-x-0',
            horizontal:
              '{screen}:space-y-0 {screen}:flex {screen}:justify-between {screen}:items-center',
          })
        "
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
          :class="
            layoutClasses({
              stacked: '{screen}:flex {screen}:flex-col {screen}:space-y-3 {screen}:space-x-0',
              horizontal: '{screen}:space-y-0 {screen}:space-x-3 {screen}:flex-row',
            })
          "
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
        :class="
          layoutClasses({
            stacked: '{screen}:flex {screen}:flex-col {screen}:space-y-3 {screen}:space-x-0',
            horizontal: '{screen}:space-y-0 {screen}:space-x-3 {screen}:flex-row',
          })
        "
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
  props: ['user', 'layout'],
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
    }
  },
}
</script>