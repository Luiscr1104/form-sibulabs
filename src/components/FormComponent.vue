<template>
  <v-container>
    <div>
      <h1 class="mt-10 mb-10 indigo--text text--lighten-1">Formulario</h1>
      <v-form
        ref="form"
        v-model="valid"
        lazy-validation
        @submit="postData"
        method="post"
      >
        <v-text-field
          v-model="post.name"
          :counter="20"
          :rules="nameRules"
          label="Name"
          required
        >
        </v-text-field>

        <v-text-field
          v-model="post.lastName"
          :counter="20"
          :rules="lastNameRules"
          label="Last Name"
          required
        >
        </v-text-field>

        <v-text-field
          v-model="post.direction"
          :rules="directionRules"
          label="Direction"
          required
        ></v-text-field>

        <v-btn
          :disabled="!valid"
          color="success"
          class="mr-4 mt-5"
          @click="validate"
          type="submit"
        >
          Validate
        </v-btn>

        <v-btn color="error" class="mr-4 mt-5" @click="reset">
          Reset Form
        </v-btn>
      </v-form>
    </div>
  </v-container>
</template>
<script>
import Vue from 'vue' 
import axios from 'axios'
import VueAxios from 'vue-axios'
Vue.use(VueAxios, axios)
export default {
  name: "FormComponent",
  data: () => ({
    valid: true,
    name: "",
    nameRules: [
      (v) => !!v || "Name is required",
      (v) => (v && v.length <= 20) || "Name must be less than 20 characters",
    ],
    lastName: "",
    lastNameRules: [
      (v) => !!v || "Last Name is required",
      (v) =>
        (v && v.length <= 20) || "LastName must be less than 20 characters",
    ],
    direction: "",
    directionRules: [
      (v) => !!v || "Direction is required",
      (v) =>
        (v && v.length <= 20) || "Direction must be less than 20 characters",
    ],

    post: {
      name:null,
      lastName:null,
      direction:null,
    },
  }),
  methods: {
    postData(e) {
      this.axios.post("http://localhost:3000/post", this.post).then((result) => {
        console.warn(result);
      });
      e.preventDefault();
    },
    validate() {
      this.$refs.form.validate();
    },
    reset() {
      this.$refs.form.reset();
    },
  },
};
</script>
