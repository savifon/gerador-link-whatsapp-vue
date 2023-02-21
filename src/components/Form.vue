<script setup lang="ts">
import { SparklesIcon } from "@heroicons/vue/24/outline";
</script>

<template>
  <form action="">
    <div class="space-y-4">
      <div class="flex flex-col">
        <label for="phone">WhatsApp do destinatário*</label>
        <input
          id="phone"
          name="phone"
          type="tel"
          class="border border-gray-300 rounded-lg p-2 focus:outline-[#128c7e]"
        />
      </div>
      <div class="flex flex-col">
        <label for="message">Sua mensagem (opcional)</label>
        <textarea
          id="message"
          name="message"
          class="border border-gray-300 rounded-lg p-2 focus:outline-[#128c7e]"
        ></textarea>
      </div>
      <button
        type="submit"
        class="uppercase flex items-center justify-center gap-2 bg-[#01e675] text-white p-3 rounded-lg w-full font-medium"
      >
        <SparklesIcon class="w-6 h-6" />
        Gerar link
      </button>
    </div>
  </form>
</template>
