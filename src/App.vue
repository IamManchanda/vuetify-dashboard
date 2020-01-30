<template>
  <v-app>
    <v-content>
      <v-container class="fill-height" fluid>
        <v-row align="center" justify="center">
          <v-col cols="12" sm="8" md="4">
            <v-card width="500" class="mx-auto mt-6 pa-4">
              <v-card-title>
                <h1 class="display-1">Login</h1>
              </v-card-title>
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
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
export default {
  name: "App",
  data: () => ({
    showPasswords: true,
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
