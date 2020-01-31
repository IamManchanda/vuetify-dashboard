<template>
  <v-app>
    <v-app-bar color="primary lighten-1" app dark>
      <v-toolbar-title class="ms-4">Vuetify Dashboard</v-toolbar-title>
      <v-spacer />
      <v-btn text rounded class="me-4">
        Home
      </v-btn>
      <v-btn text rounded class="me-4">
        Login
      </v-btn>
    </v-app-bar>
    <v-content>
      <v-container class="fill-height" fluid>
        <v-row align="center" justify="center">
          <v-col cols="12" sm="8" md="6" lg="4">
            <v-card class="mx-auto mt-6">
              <v-toolbar
                class="d-flex justify-center"
                color="primary lighten-1"
                dark
                flat
              >
                <v-toolbar-title>
                  <h1 class="headline">Login</h1>
                </v-toolbar-title>
              </v-toolbar>
              <div class="pa-4">
                <v-card-text>
                  <v-form>
                    <v-text-field
                      label="Username"
                      prepend-icon="mdi-account-circle"
                    />
                    <v-text-field
                      :type="passwordEyeType"
                      label="Password"
                      prepend-icon="mdi-lock"
                      :append-icon="passwordEyeIcon"
                      @click:append="handlePasswordEyeToggle"
                    />
                  </v-form>
                </v-card-text>
                <v-card-actions>
                  <v-btn color="success">Register</v-btn>
                  <v-spacer></v-spacer>
                  <v-btn color="info">Login</v-btn>
                </v-card-actions>
              </div>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
    <v-footer color="primary lighten-1" padless>
      <v-row justify="center" no-gutters>
        <v-btn
          v-for="link in links"
          :key="link"
          color="white"
          text
          rounded
          class="my-2"
        >
          {{ link }}
        </v-btn>
        <v-col class="primary lighten-2 py-4 text-center white--text" cols="12">
          {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
        </v-col>
      </v-row>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: "App",
  data: () => ({
    showPasswords: true,
    links: ["Home", "Login"],
  }),
  computed: {
    passwordEyeType() {
      return this.showPasswords ? "password" : "text";
    },
    passwordEyeIcon() {
      return this.showPasswords ? "mdi-eye" : "mdi-eye-off";
    },
  },
  methods: {
    handlePasswordEyeToggle() {
      this.showPasswords = !this.showPasswords;
    },
  },
};
</script>
