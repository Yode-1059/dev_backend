<template>
  <div>
    <NuxtPage />
  </div>
</template>

<script setup lang="ts">
const { logout, login, user } = useUserState();
import { getAuth, onAuthStateChanged } from 'firebase/auth';
console.log('test');

let auth: any;

onMounted(() => {
  auth = getAuth();
  onAuthStateChanged(auth, (authUser) => {
    console.log(authUser, 'auth');

    if (authUser) {
      const loginUser: any = {
        uid: authUser.uid,
        displayName: authUser.displayName,
      };
      login(loginUser);
    } else {
      logout();
    }
  });
});
</script>
