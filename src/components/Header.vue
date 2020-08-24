<template>
  <div id="header">
    <b-row align-v="center">
      <b-col>
        <SignLogIn />
      </b-col>
      <b-col>
        <router-link to="/">Home</router-link>
      </b-col>
      <b-col>
        <Menu />
      </b-col>
    </b-row>
  </div>
</template>

<script>
import Menu from "./Menu.vue";
import SignLogIn from "./SignLogIn.vue";

export default {
  name: "Header",
  components: {
    Menu,
    SignLogIn,
  },
};
</script>

<style>
#header {
  background-color: black;
  text-align: center;
  vertical-align: middle;
}

.align-items-center {
  width: 100%;
}

a.router-link-active:hover {
  color: blue;
  text-decoration: none;
}
</style>