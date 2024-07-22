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
        'text-center rounded-lg border border-transparent bg-gray-400 border-gray-400 bg-white text-gray-950 shadow dark:border-gray-800 dark:bg-gray-950 dark:text-gray-50 transition-colors hover:bg-gray-50 dark:hover:bg-gray-800',
        props.class
      )
    "
  >
    <slot />
  </div>
</template>
