<template>
  <q-layout view="lHh Lpr lFf">
    <q-header>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />
      </q-toolbar>
      <div class="q-px-lg q-pt-xl q-mb-md">
        <div class="text-h3">Todo</div>
        <div class="text-subtitle1">{{ todaysDate }}</div>
      </div>
      <q-img src="arcades-3428490_1920.jpg"
             class="header-image absolute-top"
      />
    </q-header>

    <q-drawer
        v-model="leftDrawerOpen"
        show-if-above
        :width="250"
        :breakpoint="600"
    >
      <q-scroll-area style="height: calc(100% - 192px); margin-top: 192px; border-right: 1px solid #ddd">
        <q-list padding>
          <q-item
              to="/"
              exact
              clickable
              v-ripple>
            <q-item-section avatar>
              <q-icon name="list" />
            </q-item-section>
            <q-item-section>Todo</q-item-section>
          </q-item>

          <q-item
              to="/help"
              exact
              clickable
              v-ripple>
            <q-item-section avatar>
              <q-icon name="help" />
            </q-item-section>
            <q-item-section>Help</q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>

      <q-img class="absolute-top" src="arcades-3428490_1920.jpg" style="height: 192px">
        <div class="absolute-bottom bg-transparent">
          <q-avatar size="56px" class="q-mb-sm">
            <img src="http://gravatar.com/avatar/b5e9751563c4bf981b8ce43924966a40">
          </q-avatar>
          <div class="text-weight-bold">Jefferson Costa</div>
          <div>@jscosta</div>
        </div>
      </q-img>
    </q-drawer>

    <q-page-container>
      <keep-alive>
        <router-view />
      </keep-alive>
    </q-page-container>
  </q-layout>
</template>

<script>
import { date } from 'quasar'

const linksData = [
  {
    title: 'Docs',
    caption: 'quasar.dev',
    icon: 'school',
    link: 'https://quasar.dev'
  },
  {
    title: 'Github',
    caption: 'github.com/quasarframework',
    icon: 'code',
    link: 'https://github.com/quasarframework'
  },
  {
    title: 'Discord Chat Channel',
    caption: 'chat.quasar.dev',
    icon: 'chat',
    link: 'https://chat.quasar.dev'
  },
  {
    title: 'Forum',
    caption: 'forum.quasar.dev',
    icon: 'record_voice_over',
    link: 'https://forum.quasar.dev'
  },
  {
    title: 'Twitter',
    caption: '@quasarframework',
    icon: 'rss_feed',
    link: 'https://twitter.quasar.dev'
  },
  {
    title: 'Facebook',
    caption: '@QuasarFramework',
    icon: 'public',
    link: 'https://facebook.quasar.dev'
  },
  {
    title: 'Quasar Awesome',
    caption: 'Community Quasar projects',
    icon: 'favorite',
    link: 'https://awesome.quasar.dev'
  }
]

export default {
  name: 'MainLayout',
  components: { },
  data () {
    return {
      leftDrawerOpen: false,
      essentialLinks: linksData
    }
  },
  computed: {
    todaysDate () {
      return date.formatDate(Date.now(), 'dddd D MMMM')
    }
  }
}
</script>

<style lang="stylus">
.header-image
  height 100%
  z-index -1
  opacity 0.2
  filter grayscale(100%)
</style>
