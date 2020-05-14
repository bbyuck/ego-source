<template>
  <v-ons-page class="start_view">
    <login-page v-on:kakaoLogin="temporary_start"></login-page>
  </v-ons-page>
</template>

<script>
import LoginPage from "./LoginPage.vue";

export default {
  components: {
    LoginPage
  },
  methods: {
    temporary_start: function () {
      this.$emit("start");
    }
  }
}
</script>

<style>
.start_view {
  overflow: hidden;
}
</style>