<script setup lang="ts">
import { ref } from "vue";
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import HelloWorld from "./components/HelloWorld.vue";
const content = ref("");
</script>

<template>
  <HelloWorld v-model="content" />
</template>

<style scoped></style>
