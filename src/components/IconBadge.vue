<script>
import { h, cloneVNode } from 'vue'

export default {
  // <span class="flex items-center space-x-2">
  //   <BadgeCheckIcon class="h-5 w-5 text-gray-400" />
  //   <span class="text-sm text-gray-500 leading-5 font-medium">
  //     Pro Member
  //   </span>
  // </span>
  setup(props, { slots }) {
    const [icon, text] = slots.default()

    return () =>
      h(
        'span',
        {
          class: 'flex items-center space-x-2',
        },
        [
          cloneVNode(icon, {
            class: 'h-5 w-5 text-gray-400',
          }),
          cloneVNode(text, {
            class: 'text-sm text-gray-500 leading-5 font-medium',
          }),
        ]
      )
  },
}
</script>