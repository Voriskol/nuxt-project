<script setup lang="ts">
import type { HTMLAttributes } from "vue";
import { cn } from "@/utils";

const props = defineProps<{
  class?: HTMLAttributes["class"];
}>();
</script>

<template>
  <div
    :class="
      cn(
        'text-center rounded-lg border text-gray-900 hover:text-gray-300 border-transparent bg-gray-50 border-purple-400 p-5 hover:bg-gray-500 hover:border-gray-500 transition-all',
        props.class
      )
    "
  >
    <slot />
  </div>
</template>
