<template>
  <div v-if="user.uid">
    <p class="text-3xl font-bold underline">{{ user.displayName }}</p>
    <Post />
  </div>
  <div v-else>
    <Auth />
  </div>
</template>

<script setup lang="ts">
const { user } = useUserState();

import Auth from './auth.vue'
import Post from './post.vue';

</script>
