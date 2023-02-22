<script setup lang="ts">
import BaseHeader from "@/components/BaseHeader.vue";
import BaseFooter from "@/components/BaseFooter.vue";
import LinkGenerator from "@/components/LinkGenerator.vue";
</script>

<template>
  <BaseHeader />

  <main class="p-4">
    <LinkGenerator />
  </main>

  <BaseFooter />
</template>
