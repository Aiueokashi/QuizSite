<template>
  <v-app dark>
    <v-navigation-drawer v-model="drawer" fixed app>
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
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar fixed app flat color="primary">
      <v-app-bar-nav-icon dark @click.stop="drawer = !drawer" />
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    <v-footer :absolute="!fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data() {
    return {
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: '最初のページ',
          to: '/',
        },{
          icon: 'mdi-table-of-contents',
          title:'芳香族化合物',
          to: '/list/aroma',
        },{
          icon: 'mdi-crosshairs-question',
          title: '芳香族化合物',
          to: '/question/aroma',
        },{
          icon: 'mdi-account-hard-hat',
          title:'テスト',
          to: '/test'
        }
      ],
      title: 'Vuetify.js',
    }
  },
}
</script>
