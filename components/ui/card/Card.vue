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
        'rounded-lg border border-transparent border-gray-400 bg-white text-gray-950 shadow dark:border-gray-800 dark:bg-gray-950 dark:text-gray-50 transition-colors hover:bg-gray-50 dark:hover:bg-gray-800',
        props.class
      )
    "
  >
    <slot />
  </div>
</template>

<style scoped>
@keyframes show {
  from {
    @apply border-gray-400;
    opacity: 0.4;
    transform: scale(0.8) translateY(-30px);
  }

  90% {
    @apply border-gray-400;
  }

  to {
    @apply border-transparent;
    transform: scale(1) translateY(0);
    opacity: 1;
  }
}
</style>
