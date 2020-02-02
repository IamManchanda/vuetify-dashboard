<template>
  <v-app>
    <v-app-bar color="primary lighten-1" app dark>
      <v-toolbar-title class="ms-4">
        {{ title }}
      </v-toolbar-title>
      <v-spacer />
      <v-btn
        v-for="link in links"
        :key="`header-link-${link.id}`"
        text
        rounded
        class="me-4"
        :to="link.url"
      >
        {{ link.label }}
      </v-btn>
      <div class="mt-5 mx-5 v-switch-custom-container">
        <v-switch
          color="white"
          v-model="dark_theme"
          @change="toggleTheme"
          label="Dark Theme"
        />
      </div>
    </v-app-bar>
    <v-content>
      <router-view></router-view>
    </v-content>
    <v-footer color="primary lighten-1" padless>
      <v-row justify="center" no-gutters>
        <v-btn
          v-for="link in links"
          :key="`footer-link-${link.id}`"
          color="white"
          text
          rounded
          class="my-2"
          :to="link.url"
        >
          {{ link.label }}
        </v-btn>
        <v-col class="primary lighten-2 py-4 text-center white--text" cols="12">
          <v-icon dark>mdi-copyright</v-icon>
          <span>
            {{ new Date().getFullYear() }} —
            <strong>{{ title }}</strong>
          </span>
        </v-col>
      </v-row>
    </v-footer>
  </v-app>
</template>

<script>
import uuidv4 from "uuid/v4";

export default {
  name: "App",
  data: () => ({
    title: "Vuetify Dashboard",
    dark_theme: false,
    links: [
      { id: uuidv4(), label: "Dashboard", url: "/" },
      { id: uuidv4(), label: "Login", url: "/login" },
      { id: uuidv4(), label: "Signup", url: "/signup" },
    ],
  }),
  methods: {
    toggleTheme() {
      this.$vuetify.theme.dark = this.dark_theme;
    },
  },
};
</script>

<style lang="scss">
.v-switch-custom-container {
  .theme--dark.v-label {
    color: white !important;
  }
}
</style>
