<template>
  <v-container>
    <div>
      <h1 class="mt-10 mb-10 indigo--text text--lighten-1"
      >Formulario</h1>
      <v-form ref="form" v-model="valid" lazy-validation>
        <v-text-field
          v-model="name"
          :counter="20"
          :rules="nameRules"
          label="Name"
          required
        >
        </v-text-field>

        <v-text-field
          v-model="lastName"
          :counter="20"
          :rules="lastNameRules"
          label="Apellido"
          required
        >
        </v-text-field>

        <v-text-field
          v-model="email"
          :rules="emailRules"
          label="E-mail"
          required
        ></v-text-field>

        <v-select
          v-model="select"
          :items="items"
          :rules="[(v) => !!v || 'Item is required']"
          label="Item"
          required
        ></v-select>

        <v-checkbox
          v-model="checkbox"
          :rules="[(v) => !!v || 'You must agree to continue!']"
          label="Do you agree?"
          required
        ></v-checkbox>

        <v-btn
          :disabled="!valid"
          color="success"
          class="mr-4"
          @click="validate"
        >
          Validate
        </v-btn>

        <v-btn color="error" class="mr-4" @click="reset"> Reset Form </v-btn>
      </v-form>
    </div>
  </v-container>
</template>
<script>
export default {
  name: "FormComponent",

  data: () => ({
    valid: true,
    name: "",
    nameRules: [
      (v) => !!v || "Name is required",
      (v) => (v && v.length <= 20) || "Name must be less than 10 characters",
    ],
    lastName: "",
    lastNameRules: [
      (v) => !!v || "Last Name is required",
      (v) => (v && v.length <= 20) || "LastName must be less than 10 characters",
    ],
    email: "",
    emailRules: [
      (v) => !!v || "E-mail is required",
      (v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
    ],
    select: null,
    items: ["Item 1", "Item 2", "Item 3", "Item 4"],
    checkbox: false,
  }),
  methods: {
      validate () {
        this.$refs.form.validate()
      },
      reset () {
        this.$refs.form.reset()
      },
    },
};
</script>