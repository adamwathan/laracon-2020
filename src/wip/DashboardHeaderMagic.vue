<template>
  <div class="flex items-center justify-between">
    <div class="flex-1 space-y-8">
      <div
        :class="
          layoutClasses({
            stacked: 'block space-y-8',
            horizontal: 'flex justify-between items-center space-y-0',
          })
        "
      >
        <!-- Profile -->
        <div class="flex items-center space-x-3">
          <div class="flex-shrink-0 h-12 w-12">
            <img
              class="h-12 w-12 rounded-full"
              src="https://images.unsplash.com/photo-1517365830460-955ce3ccd263?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=256&h=256&q=80"
              alt=""
            />
          </div>
          <div class="space-y-1">
            <div class="text-sm leading-5 font-medium text-gray-900">Debbie Lewis</div>
            <a href="#" class="group flex items-center space-x-2.5">
              <GitHubIcon class="w-5 h-5 text-gray-400 group-hover:text-gray-500" />
              <div class="text-sm leading-5 text-gray-500 group-hover:text-gray-900 font-medium">
                debbielewis
              </div>
            </a>
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
          <Button color="indigo">New Project</Button>
          <Button color="white">Invite Team</Button>
        </div>
      </div>
      <!-- Meta info -->
      <div
        :class="
          layoutClasses({
            stacked: 'flex flex-col space-y-6 space-x-0',
            horizontal: 'flex-row space-y-0 space-x-8',
          })
        "
      >
        <div class="flex items-center space-x-2">
          <BadgeCheckIcon class="h-5 w-5 text-gray-400" />
          <span class="text-sm text-gray-500 leading-5 font-medium">Pro Member</span>
        </div>
        <div class="flex items-center space-x-2">
          <CollectionIcon class="h-5 w-5 text-gray-400" />
          <span class="text-sm text-gray-500 leading-5 font-medium">8 Projects</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Button from './Button.vue'
import BadgeCheckIcon from 'heroicons/vue/solid/BadgeCheck'
import CollectionIcon from 'heroicons/vue/solid/Collection'
import GitHubIcon from './GitHubIcon.vue'

export default {
  props: ['layout'],
  components: {
    Button,
    BadgeCheckIcon,
    CollectionIcon,
    GitHubIcon,
  },
  setup(props) {
    return {
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