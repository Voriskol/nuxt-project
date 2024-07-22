<script setup lang="ts">
import type { HTMLAttributes } from "vue";
import { cn } from "@/utils";

const props = defineProps<{
  class?: HTMLAttributes["class"];
}>();
</script>

<template>
  <div
    :class="cn('flex flex-col gap-y-1.5 p-3 pb-0 font-semibold', props.class)"
  >
    <slot />
  </div>
</template>
