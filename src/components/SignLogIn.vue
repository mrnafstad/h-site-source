<template>
  <div id="mark">
    <div v-if=" !auth">
      <button class="login" @click="setlogin">Logg inn</button>
    </div>
    <div v-if="auth">
      <p v-if="user.displayName">{{ user.displayName }}</p>
      <p v-else>{{ user.email }}</p>
      <button class="login" @click="signOut">Sign out</button>
    </div>

    <div id="login-box" v-if="login">
      Log inn with your email
      <p>
        Email:
        <input v-model="usremailL" placeholder="email@address.com" />
      </p>

      <p>
        Password:
        <input
          @keyup.enter="submitLogin"
          type="password"
          v-model="passwordL"
          placeholder="password"
        />
      </p>

      <b-row align-h="end">
        <b-col cols="2">
          <button id="con" @click="submitLogin">Submit</button>
        </b-col>
        <b-col cols="5">
          <button id="con" @click="login = false">Cancel</button>
        </b-col>
      </b-row>
    </div>
  </div>
</template>

<script>
import { mapActions, mapGetters } from "vuex";

export default {
  name: "SignLogIn",
  data() {
    return {
      login: false,
      passwordL: "",
      usremailL: "",
    };
  },
  methods: {
    ...mapActions(["authentication", "logOut", "signUp"]),
    setlogin() {
      this.login = !this.login;
      this.signup = false;
    },
    submitLogin() {
      //console.log(this.passwordL, this.usremailL)
      this.authentication({
        email: this.usremailL,
        password: this.passwordL,
      });
      this.login = !this.login;
    },
    signOut() {
      this.logOut();
    },
  },
  computed: {
    ...mapGetters(["auth", "user"]),
  },
};
</script>

<style>
button {
  border: none;
  background-color: black;
}
.login {
  color: red;
}
.signup {
  color: blue;
}
#login-box {
  position: fixed;
  left: 0%;
  top: 5%;
  background: snow;
  border-style: solid;
  border-color: black;
  border-radius: 5px;
  padding: 5px;
  text-align: center;
  width: 300px;
}
#con {
  border-radius: 5px;
  background-color: gainsboro;
  border-style: solid;
  border-color: lightgrey;
}

#con:hover {
  background-color: rgb(248, 161, 161);
}
</style>
