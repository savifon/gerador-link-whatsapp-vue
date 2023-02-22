<script setup lang="ts">
import { InformationCircleIcon } from "@heroicons/vue/24/solid";
import LinkForm from "@/components/LinkForm.vue";
</script>

<template>
  <div class="w-full max-w-[300px] mx-auto space-y-4">
    <LinkForm />
    <p class="flex items-center gap-1 text-xs text-gray-600">
      <InformationCircleIcon class="w-5 h-5" />
      Nenhum dado digitado é armazenado
    </p>
  </div>
</template>
