<template>
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
</template>

<script>
export default {
  props: ['activityItems'],
  components: {},
  setup() {
    //...
  },
}
</script>