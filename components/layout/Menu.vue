<script setup lang="ts">
import { MENU_DATA } from "./menu.data";
</script>

<template>
  <div>
    <NuxtLink
      v-for="item in MENU_DATA"
      :key="item.name"
      :to="item.url"
      class="flex items-center text-gray-700 py-1 px-3 rounded-lg w-full hover:bg-gray-700 hover:text-white hover:shadow transition-all mb-2 text-lg"
    >
      <Icon :name="item.icon" class="mr-3" />
      <span>{{ item.name }}</span>
    </NuxtLink>
  </div>
</template>
