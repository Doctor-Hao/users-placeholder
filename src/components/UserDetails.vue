<template>
  <v-form>
    <v-row>
      <v-col cols="3.9">
        <h3 class="text-grey ml-1 mb-3 font-weight-regular">ADDRESS</h3>
        <v-text-field v-model="localUser.address.street" label="Street"/>
        <v-text-field v-model="localUser.address.suite" label="Suite"/>
        <v-text-field v-model="localUser.address.city" label="City"/>
        <v-text-field v-model="localUser.address.zipcode" label="Zipcode"/>
      </v-col>

      <v-col cols="3.9">
        <h3 class="text-grey ml-1 mb-3 font-weight-regular">COMPANY</h3>
        <v-text-field v-model="localUser.company.name" label="Company Name"/>
        <v-text-field v-model="localUser.company.catchPhrase" label="Catch Phrase"/>
        <v-text-field v-model="localUser.company.bs" label="BS"/>
      </v-col>

      <v-col cols="3.9">
        <h3 class="text-grey ml-1 mb-3 font-weight-regular">BASIC INFO</h3>
        <v-text-field v-model="localUser.name" label="Name"/>
        <v-text-field v-model="localUser.username" label="Username"/>
        <v-text-field v-model="localUser.email" label="Email"/>
        <v-text-field v-model="localUser.phone" label="Phone"/>
        <v-text-field v-model="localUser.website" label="Website"/>
      </v-col>

      <v-col cols="1">
        <v-btn
            @click="saveChanges"
            class="bg-yellow save-btn"
        >
          <v-icon>
            <svg width="21" height="20" viewBox="0 0 21 20" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M1.50781 10.4894L8.76326 18.0293C9.22838 18.5126 10.0281 18.41 10.3561 17.8249L19.227 2"
                    stroke="#5F7465" stroke-width="3" stroke-linecap="round"/>
            </svg>
          </v-icon>
        </v-btn>
      </v-col>
    </v-row>

  </v-form>
</template>

<script setup lang="ts">
import {ref} from 'vue';
import {User} from "@/types/User";


interface IProps {
  user: User
}

const props = defineProps<IProps>()

const emit = defineEmits<{
  (e: 'save', user: User): void
}>()

const localUser = ref<User>({...props.user});

const saveChanges = () => {
  emit('save', localUser.value);
};

</script>

<style scoped>
.save-btn {
  width: 40px;
  height: 40px;
  min-width: 40px
}
</style>
