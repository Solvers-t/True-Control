<template>
  <v-container align="center">
    <v-row align="center">
      <v-col cols="12" sm="6"
        ><v-text-field
          v-model="login"
          hint="Email"
          label="Login"
        ></v-text-field>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" sm="6"
        ><v-text-field
          v-model="password"
          type="password"
          label="Senha"
        ></v-text-field>
      </v-col>
    </v-row>
    <v-btn @click="signIn(login, password)">texto</v-btn>
  </v-container>
</template>
<script>
export default {
  name: "HelloWorld",

  data: () => ({
    login: "",
    password: "",
  }),
  methods: {
    async signIn(login, password) {
      const axios = require("axios");
      await axios
        .get("https://5ffdc17fd9ddad0017f687fc.mockapi.io/api/v1/users", {
          params: {
            email: login,
          },
        })
        .then(function (response) {
          const userResponse = response.data[0];
          if (userResponse.password != password) {
            console.log("Senha inválida");
          } else {
            this.$emit('autenticated', true)
          }
        })
        .catch(function (error) {
          console.log(error);
        });
    },
  },
};
</script>
