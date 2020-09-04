<template>
  <DashboardLayout>
    <template #header>
      <Navbar />

      <div class="bg-white">
        <div class="max-w-7xl w-full mx-auto p-8">
          <DashboardHeaderMagic :user="user" :layout="{ default: 'stacked', sm: 'horizontal' }" />
        </div>
      </div>
    </template>
    <template #leftColumn>
      <DashboardHeaderMagic
        :user="user"
        :layout="{ default: 'stacked', sm: 'horizontal', xl: 'stacked' }"
      />
    </template>
    <template #centerColumn>
      <ProjectList :projects="projects" />
    </template>
    <template #rightColumn>
      <ActivityFeed :activityItems="activityItems" />
    </template>
  </DashboardLayout>
</template>

<script>
import DashboardLayout from './DashboardLayout.vue'
import Navbar from './Navbar.vue'
import DashboardHeader from './DashboardHeader.vue'
import DashboardHeaderMagic from './DashboardHeaderMagic.vue'
import ProjectList from './ProjectList.vue'
import ActivityFeed from './ActivityFeed.vue'

export default {
  components: {
    Navbar,
    DashboardLayout,
    DashboardHeader,
    DashboardHeaderMagic,
    ProjectList,
    ActivityFeed,
  },
  setup(props) {
    return {
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


<!--
  <DashboardHeaderMagic
    :user="user"
    :layout="{ default: 'stacked', sm: 'horizontal', xl: 'stacked' }"
  />
-->

<!--
  <div class="bg-white">
    <div class="max-w-7xl w-full mx-auto p-8">
      <DashboardHeaderMagic :user="user" :layout="{ default: 'stacked', sm: 'horizontal' }" />
    </div>
  </div>
-->