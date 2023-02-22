<script setup lang="ts">
import {
  PaperAirplaneIcon,
  DocumentDuplicateIcon,
  ArrowPathIcon,
} from "@heroicons/vue/24/solid";
import { computed, ref } from "vue";

const phoneNumber = ref("");
const message = ref("");
const generatedLink = computed(
  () => `https://wa.me/${phoneNumber.value}?text=${message.value}`
);
const isValid = computed(() => phoneNumber.value.length > 10);

const resetForm = () => {
  phoneNumber.value = "";
  message.value = "";
};

const copyLink = () => {
  navigator.clipboard.writeText(generatedLink.value);
};
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
          placeholder="55 27 8765 4321"
          required
          v-model="phoneNumber"
          class="border border-gray-300 rounded-lg p-2 focus:outline-[#128c7e]"
        />
      </div>
      <div class="flex flex-col">
        <label for="message">Sua mensagem (opcional)</label>
        <textarea
          id="message"
          name="message"
          v-model="message"
          class="border border-gray-300 rounded-lg p-2 focus:outline-[#128c7e]"
        ></textarea>
      </div>

      <div
        class="border border-dashed border-gray-300 bg-gray-50 rounded-lg space-y-4 p-4"
        :class="[!isValid && 'opacity-30']"
      >
        <div
          class="relative flex items-center h-11 border border-gray-300 bg-gray-100 rounded-lg overflow-hidden"
        >
          <span
            class="w-10/12 line-clamp-1 flex items-center pl-2 text-xs bg-transparent inset-0 outline-none cursor-default"
            :class="[!isValid && 'select-none']"
          >
            {{ generatedLink.replace("https://", "") }}
          </span>
          <button
            type="button"
            class="absolute flex items-center justify-center w-11 h-full top-0 right-0 text-white bg-[#01e675] border-l border-l-gray-300"
            :disabled="!isValid"
            @click="copyLink"
          >
            <DocumentDuplicateIcon class="w-6 h-6" />
          </button>
        </div>
        <a
          :href="isValid ? generatedLink : '#'"
          target="_blank"
          class="uppercase flex items-center justify-center gap-2 bg-[#01e675] text-white p-3 rounded-lg w-full font-medium"
          :class="[!isValid && 'cursor-not-allowed']"
          @click="(e) => !isValid && e.preventDefault()"
        >
          <PaperAirplaneIcon class="w-6 h-6" />
          Acessar link
        </a>
        <button
          type="reset"
          class="uppercase flex items-center justify-center gap-2 bg-gray-200 text-gray-700 p-3 rounded-lg w-full font-medium"
          :disabled="!isValid"
          @click="resetForm"
        >
          <ArrowPathIcon class="w-6 h-6" />
          Gerar novo link
        </button>
      </div>
    </div>
  </form>
</template>
