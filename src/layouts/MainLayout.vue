<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          ATSFlex
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
    >
      <q-list>
        <q-item-label
          header
        >
          Essential Links
        </q-item-label>

        <EssentialLink
          v-for="link in linksList"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

defineOptions({
  name: 'MainLayout'
})

const linksList = [
  {
    title: 'Batches',
    icon: 'settings',
    link: 'https://quasar.dev'
  },
  {
    title: 'External Batches',
    icon: 'settings',
    link: 'https://github.com/quasarframework'
  },
  {
    title: 'Materials',
    icon: 'print',
    link: 'https://chat.quasar.dev'
  },
  {
    title: 'Packaging Orders',
    icon: 'print',
    link: 'https://forum.quasar.dev'
  },
  {
    title: 'New Packaging Order',
    icon: 'add_circle',
    link: 'https://twitter.quasar.dev'
  },
  {
    title: 'Aggregation Station',
    icon: 'share',
    link: 'https://facebook.quasar.dev'
  },
  {
    title: 'Quality Control',
    icon: 'group',
    link: 'https://awesome.quasar.dev'
  },
  {
    title: 'Rework Orders',
    icon: 'sync_alt',
    link: 'https://awesome.quasar.dev'
  },
    {
    title: 'Rework Station',
    icon: 'account_tree',
    link: 'https://awesome.quasar.dev'
  },
  {
    title: 'Settings',
    icon: 'settings_suggest',
    link: 'https://awesome.quasar.dev'
  }
]

const leftDrawerOpen = ref(false)

function toggleLeftDrawer () {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>
