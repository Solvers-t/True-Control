<template>
 <!-- App.vue -->

<v-app>
  <v-navigation-drawer app>
    <!-- -->
  </v-navigation-drawer>

  <v-app-bar app>
    <!-- -->
  </v-app-bar>

  <!-- Sizes your content based upon application components -->
  <v-main>

    <!-- Provides the application the proper gutter -->
    <v-container fluid>
      <login v-if="!isAutenticated" @autenticated="autenticated"/>
      <!-- If using vue-router -->
    </v-container>
  </v-main>

  <v-footer app>
    <!-- -->
  </v-footer>
</v-app>
</template>

<script>

import Login from './components/Login.vue';

export default {
  name: 'App',

  components: {
    Login,
  },

  data: () => ({
    isAutenticated: false,
  }),
  methods: {
    autenticated(autenticated) {
      this.isAutenticated=autenticated;
    }
  }
};
</script>
