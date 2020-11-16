<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      :clipped="clipped"
      fixed
      temporary
      app
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="`drawer_nav_item_${i}`"
          :to="item.to"
          :href="item.href"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar :clipped-left="clipped" flat app>
      <v-app-bar-nav-icon
        @click.stop="drawer = !drawer"
        class="hidden-sm-and-up"
      />
      <v-toolbar-title v-text="title" />

      <v-spacer />

      <v-toolbar-items class="hidden-xs-only">
        <template v-for="(item, i) in items">
          <v-btn
            text
            v-bind:key="`toolbar_item_${i}_btn`"
            :to="items[i].to"
            :href="items[i].href"
          >
            {{ items[i].title }}
          </v-btn>
        </template>
      </v-toolbar-items>
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <v-footer absolute app>
      <v-col class="text-center">
        <span class="blue-grey-darken-4--text">
          &copy; {{ new Date().getFullYear() }}
          <a
            href="https://huhubun.com/"
            class="text-decoration-none blue-grey--text text--darken-4"
          >
            huhubun
          </a>
        </span>
      </v-col>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: true,
      drawer: false,
      items: [
        {
          icon: 'mdi-home-outline',
          title: '首页',
          to: '/'
        },
        {
          icon: 'mdi-information-outline',
          title: '博客',
          href: 'https://bun.plus/'
        },
        {
          icon: 'mdi-information-outline',
          title: '作品',
          href: 'https://bun.dev/'
        },
        {
          icon: 'mdi-information-outline',
          title: '导航',
          href: 'https://huhubun.com/'
        }
      ],
      title: '呼呼小笼包的介绍'
    }
  }
}
</script>
