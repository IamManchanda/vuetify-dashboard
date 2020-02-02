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
            <v-form @submit.prevent="submit">
              <v-card-text>
                <v-text-field
                  v-model="username"
                  :counter="10"
                  label="Username"
                  color="primary"
                  prepend-icon="mdi-account-circle"
                  :error-messages="username_errors"
                  required
                  @input="$v.username.$touch()"
                  @blur="$v.username.$touch()"
                />
                <v-text-field
                  v-model="email"
                  label="Email"
                  type="email"
                  color="primary"
                  prepend-icon="mdi-email"
                  :error-messages="email_errors"
                  required
                  @input="$v.email.$touch()"
                  @blur="$v.email.$touch()"
                />
                <v-autocomplete
                  v-model="selected_browser"
                  label="Which Browser do you use"
                  color="primary"
                  prepend-icon="mdi-edge"
                  :items="browsers"
                  :error-messages="selected_browser_errors"
                  required
                  @change="$v.selected_browser.$touch()"
                  @blur="$v.selected_browser.$touch()"
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
                  v-model="tnc"
                  label="Agree with terms and conditions"
                  color="primary"
                  :error-messages="tnc_errors"
                  required
                  @change="$v.tnc.$touch()"
                  @blur="$v.tnc.$touch()"
                />
              </v-card-text>
              <v-card-actions class="d-flex justify-center">
                <div class="my-2">
                  <v-btn type="submit" color="primary" class="me-4" dark large>
                    Submit
                  </v-btn>
                  <v-btn @click="clear" dark large>
                    Clear
                  </v-btn>
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
import { validationMixin } from "vuelidate";
import { required, maxLength, email } from "vuelidate/lib/validators";

export default {
  name: "Signup",
  mixins: [validationMixin],
  data: () => ({
    date: new Date().toISOString().substr(0, 10),
    menu: false,
    browsers: ["Chrome", "Safari", "Firefox", "Edge", "Opera", "Brave"],
    username: "",
    email: "",
    selected_browser: null,
    tnc: false,
  }),
  validations: {
    username: { required, maxLength: maxLength(10) },
    email: { required, email },
    selected_browser: { required },
    tnc: {
      checked(val) {
        return val;
      },
    },
  },
  computed: {
    username_errors() {
      const errors = [];
      if (!this.$v.username.$dirty) return errors;
      !this.$v.username.maxLength &&
        errors.push("Username must be at most 10 characters long");
      !this.$v.username.required && errors.push("Username is required.");
      return errors;
    },
    email_errors() {
      const errors = [];
      if (!this.$v.email.$dirty) return errors;
      !this.$v.email.email && errors.push("Must be valid e-mail");
      !this.$v.email.required && errors.push("E-mail is required");
      return errors;
    },
    selected_browser_errors() {
      const errors = [];
      if (!this.$v.selected_browser.$dirty) return errors;
      !this.$v.selected_browser.required && errors.push("Browser is required");
      return errors;
    },
    tnc_errors() {
      const errors = [];
      if (!this.$v.tnc.$dirty) return errors;
      !this.$v.tnc.checked && errors.push("You must agree to continue!");
      return errors;
    },
  },
  methods: {
    submit() {
      this.$v.$touch();
    },
    clear() {
      this.$v.$reset();
      this.username = "";
      this.email = "";
      this.selected_browser = null;
      this.tnc = false;
    },
  },
};
</script>
