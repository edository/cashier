<template>
  <v-app dark>
    <v-navigation-drawer v-model="sideDrawer" fixed app>
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar :clipped-left="clipped" fixed app>
      <v-app-bar-nav-icon @click.stop="sideDrawer = !sideDrawer" />
      <v-toolbar-title>{{ title }}</v-toolbar-title>
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    <v-bottom-navigation>
      <v-app-bar-nav-icon>
        <v-btn v-for="(item, i) in bottomMenu"> </v-btn>
      </v-app-bar-nav-icon>
    </v-bottom-navigation>
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data() {
    return {
      sideDrawer: false,
      items: [
        {
          icon: 'mdi-application',
          title: 'App',
          to: '/',
        },
        {
          icon: 'mdi-account',
          title: 'Account',
          to: '/account',
        },
        {
          icon: 'mdi-bell',
          title: 'Notification',
          to: '/notification',
        },
      ],
      right: true,
      rightDrawer: false,
      title: 'Cashier',
    }
  },
}
</script>
