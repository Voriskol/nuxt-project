<script lang="ts" setup>
import { account } from "@/utils/appwrite";
import { useAuthStore, useIsLoadingStore } from "@/store/auth.store";

const isLoadingStore = useIsLoadingStore();
const authStore = useAuthStore();
const router = useRouter();

async function logout() {
  isLoadingStore.set(true);
  await account.deleteSession("current");
  authStore.clear();
  router.push("/login");
  isLoadingStore.set(false);
}
</script>

<template>
  <aside
    class="px-5 py-8 bg-gray-300 h-full relative w-full border-r-2 border-purple-400"
  >
    <NuxtLink to="/" class="mb-10 block">
      <NuxtImg src="/logo.png" alt="Logo" width="120px" class="mx-auto" />
    </NuxtLink>
    <button
      @click="logout"
      class="absolute top-2 right-2 hover:text-purple-400 transition"
    >
      <Icon name="line-md:logout" size="20px" />
    </button>
    <LayoutMenu />
  </aside>
</template>
