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
    signIn(login, password) {
      console.log(login, password);
      const axios = require("axios");
      axios
        .get("https://5fe22f647a94870017682293.mockapi.io/Users", {
          params: {
            email: login,
          },
        })
        .then(function (response) {
          const userResponse = response.data[0]
          if (userResponse.password!=password) {
            console.log("Senha inválida");
          }
          console.log(response.data);
        })
        .catch(function (error) {
          console.log(error);
        })
        .then(function () {
          // always executed
        });
    },
  },
};
</script>
