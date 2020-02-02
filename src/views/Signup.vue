<template>
  <v-container class="fill-height" fluid>
    <v-row align="center" justify="center">
      <v-col cols="12" sm="8" md="6" lg="4">
        <v-card class="mx-auto mt-6">
          <v-toolbar class="d-flex justify-center" color="primary" dark flat>
            <v-toolbar-title>
              <h1 class="headline">Signup</h1>
            </v-toolbar-title>
          </v-toolbar>
          <div class="pa-4">
            <v-form>
              <v-card-text>
                <v-text-field
                  label="Email"
                  type="email"
                  color="primary"
                  prepend-icon="mdi-email"
                />
                <v-autocomplete
                  label="Which Browser do you use"
                  color="primary"
                  prepend-icon="mdi-edge"
                  :items="browsers"
                />
                <v-file-input label="Attach Profile Picture" color="primary" />
              </v-card-text>
              <v-card-actions class="d-flex justify-center">
                <div class="my-2">
                  <v-btn color="primary" dark large>Submit</v-btn>
                </div>
              </v-card-actions>
            </v-form>
          </div>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "Signup",
  data: () => ({
    browsers: ["Chrome", "Safari", "Firefox", "Edge", "Opera", "Brave"],
  }),
  computed: {},
  methods: {},
};
</script>
