<template>
  <div class="px-5 mt-8">
    <v-row class="d-flex header-list text-grey mb-1">
      <v-col>Name</v-col>
      <v-col>Email</v-col>
      <v-col>Phone</v-col>
      <v-col>Website</v-col>
    </v-row>
    <v-expansion-panels variant="accordion">
      <v-expansion-panel
          v-for="user in users"
          :key="user.id"
          class="mb-3"
      >
        <v-expansion-panel-title
            class="panel pa-2 pl-1"
        >
          <template v-slot:actions>
            <v-icon size="40" class="icon color-action">$expand</v-icon>
          </template>
          <v-row class="header ml-3">
            <v-col>{{ user.name }}</v-col>
            <v-col>{{ user.email }}</v-col>
            <v-col>{{ user.phone }}</v-col>
            <v-col>{{ user.website }}</v-col>
          </v-row>
        </v-expansion-panel-title>

        <v-expansion-panel-text class="mt-5">
          <UserDetails :user="user" @save="saveUser"/>
        </v-expansion-panel-text>
      </v-expansion-panel>
    </v-expansion-panels>
  </div>
</template>

<script setup lang="ts">
import {ref, onMounted} from 'vue';
import {getUsers} from '@/services/userService';
import UserDetails from './UserDetails.vue';
import {User} from "@/types/User";


const users = ref<User[]>();

onMounted(async () => {
  const response = await getUsers();
  users.value = response.data
});

const saveUser = (updatedUser: User) => {
  alert(`Измененные данные: ${JSON.stringify(updatedUser)}`);
};

</script>

<style scoped>
.icon {
  order: 0;
}

.header {
  order: 1;

}

.panel {
  border: 2px solid var(--yellow-bg-color);
}

.color-action {
  color: var(--yellow-bg-color);
  width: 20px;
  height: 20px;
}

.header-list {
  padding-left: 4.5em;
}
</style>
