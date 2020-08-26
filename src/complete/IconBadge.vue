<script>
import { h, cloneVNode } from 'vue'

export default {
  props: ['href'],
  setup(props, { slots }) {
    const [icon, label] = slots.default()

    return () =>
      h(
        props.href ? 'a' : 'span',
        {
          class: 'group flex items-center space-x-2',
          href: props.href,
        },
        [
          cloneVNode(icon, {
            class: `flex-shrink-0 h-5 w-5 text-gray-400 ${
              props.href ? 'group-hover:text-gray-500' : ''
            }`,
          }),
          cloneVNode(label, {
            class: `text-sm text-gray-500 leading-5 font-medium ${
              props.href ? 'group-hover:text-gray-900' : ''
            }`,
          }),
        ]
      )
  },
}
</script>