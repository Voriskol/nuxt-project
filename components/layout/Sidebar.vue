<script lang="ts" setup></script>

<template>
  <aside
    class="px-5 py-8 bg-gray-300 h-full relative w-full border-r-2 border-purple-400"
  >
    <NuxtLink to="/" class="mb-10 block">
      <NuxtImg src="/logo.png" alt="Logo" width="120px" class="mx-auto" />
    </NuxtLink>
    <button class="absolute top-2 right-2 hover:text-purple-400 transition">
      <Icon name="line-md:logout" size="20px" />
    </button>
    <LayoutMenu />
  </aside>
</template>
