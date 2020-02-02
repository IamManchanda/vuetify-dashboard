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
                <v-dialog
                  ref="dialog"
                  v-model="menu"
                  :close-on-content-click="false"
                  :nudge-right="40"
                  transition="scale-transition"
                  offset-y
                  width="290px"
                >
                  <template v-slot:activator="{ on }">
                    <v-text-field
                      v-model="date"
                      label="Picker without buttons"
                      prepend-icon="mdi-calendar"
                      color="primary"
                      readonly
                      v-on="on"
                    />
                  </template>
                  <v-date-picker
                    v-model="date"
                    @input="menu = false"
                    scrollable
                  />
                </v-dialog>
                <v-checkbox
                  label="Agree with terms and conditions"
                  color="primary"
                />
              </v-card-text>
              <v-card-actions class="d-flex justify-center">
                <div class="my-2">
                  <v-btn type="submit" color="primary" dark large>Submit</v-btn>
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
    date: new Date().toISOString().substr(0, 10),
    menu: false,
  }),
  computed: {},
  methods: {},
};
</script>
