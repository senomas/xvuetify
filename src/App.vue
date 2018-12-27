<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="mini"
      light
      absolute
      mobile-break-point="960"
      app
      clipped
    >
      <v-toolbar flat class="transparent">
        <v-list class="pa-0">
          <v-list-tile avatar>
            <v-list-tile-avatar>
              <img src="https://randomuser.me/api/portraits/men/85.jpg">
            </v-list-tile-avatar>
            <v-list-tile-content>
              <v-list-tile-title>John Leider</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </v-list>
      </v-toolbar>
      <v-list class="pt-0" dense>
        <v-divider></v-divider>
        <v-list-tile v-for="item in items" :key="item.title" :to="item.link">
          <v-list-tile-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title>{{ item.title }}</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
      <v-footer absolute light class="pa-0 hidden-sm-and-down">
        <v-list class="pt-0" dense>
          <v-list-tile v-if="!mini" @click="mini = true">
            <v-list-tile-action>
              <v-icon>chevron_left</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>Collapse</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
          <v-list-tile v-else @click="mini = false">
            <v-list-tile-action>
              <v-icon>chevron_right</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title></v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </v-list>
      </v-footer>
    </v-navigation-drawer>
    <v-content>
      <v-toolbar dark color="primary">
        <v-toolbar-side-icon @click.stop="drawer = !drawer" dark class="hidden-md-and-up"></v-toolbar-side-icon>
        <v-toolbar-title dark>Vuetify Tutorial</v-toolbar-title>
        <v-spacer></v-spacer>
        <v-toolbar-items class="hidden-sm-and-down">
          <v-btn flat>Link One</v-btn>
          <v-btn flat>Link Two</v-btn>
          <v-btn flat>Link Three</v-btn>
        </v-toolbar-items>
      </v-toolbar>
      <router-view/>
    </v-content>
  </v-app>
</template>

<style>
.v-navigation-drawer footer > div.v-list {
  width: 100%;
}
</style>


<script>
export default {
  data() {
    return {
      items: [
        { title: "Home", icon: "dashboard", link: "/" },
        { title: "About", icon: "question_answer", link: "/about" }
      ],
      drawer: true,
      mini: false
    };
  }
};
</script>