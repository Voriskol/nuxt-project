<script setup lang="ts">
import type { ICard, IColumn } from "~/components/kanban/kanban.types.ts";
useHead({
  title: "Home",
});

const dragCard = ref<ICard | null>(null);
const sourceColumn = ref<IColumn | null>(null);
</script>

<template>
  <div class="p-10">
    <h1 class="text-3xl font-bold">My Nuxt project</h1>
    <div>
      <UiCard class="mb-3 bg-gray-300 hover:border-purple-400" draggable="true">
        <UiCardHeader role="button"> Card title </UiCardHeader>
        <UiCardContent>
          <p class="text-gray-700 dark:text-gray-400">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Accusamus
          </p>
        </UiCardContent>
      </UiCard>
    </div>
  </div>
</template>
