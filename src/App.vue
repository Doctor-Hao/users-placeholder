<template>
  <v-app>
    <v-main>
        <v-app-bar flat class="border-b-lg">
          <v-app-bar-title class="font-weight-medium text-grey">USERS</v-app-bar-title>
        </v-app-bar>
        <UserList />
    </v-main>
  </v-app>
</template>

<script setup lang="ts">
import UserList from './components/UserList.vue';

</script>

<style lang="css">
@import "assets/styles/main.css";
</style>
