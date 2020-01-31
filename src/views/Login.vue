<template>
  <v-container class="fill-height" fluid>
    <v-row align="center" justify="center">
      <v-col cols="12" sm="8" md="6" lg="4">
        <v-card class="mx-auto mt-6">
          <v-toolbar class="d-flex justify-center" color="primary" dark flat>
            <v-toolbar-title>
              <h1 class="headline">Login</h1>
            </v-toolbar-title>
          </v-toolbar>
          <div class="pa-4">
            <v-card-text>
              <v-form>
                <v-text-field
                  label="Username"
                  color="primary"
                  prepend-icon="mdi-account-circle"
                />
                <v-text-field
                  color="primary"
                  label="Password"
                  :type="passwordEyeType"
                  prepend-icon="mdi-lock"
                  :append-icon="passwordEyeIcon"
                  @click:append="handlePasswordEyeToggle"
                />
              </v-form>
            </v-card-text>
            <v-card-actions class="d-flex justify-center">
              <div class="my-2">
                <v-btn color="primary" dark large>Submit</v-btn>
              </div>
            </v-card-actions>
          </div>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "Login",
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
