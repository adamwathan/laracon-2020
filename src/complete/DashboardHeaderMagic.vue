<template>
  <div class="flex items-center justify-between">
    <div class="flex-1 space-y-8">
      <div
        :class="
          layoutClasses({
            stacked: 'block space-y-8 space-x-0',
            horizontal: 'space-y-0 flex justify-between items-center',
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
              stacked: 'flex flex-col space-y-3 space-x-0',
              horizontal: 'space-y-0 space-x-3 flex-row',
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
            stacked: 'flex flex-col space-y-3 space-x-0',
            horizontal: 'space-y-0 space-x-3 flex-row',
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