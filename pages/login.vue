<script setup lang="ts">
useHead({
  title: "Login",
});

const name = ref("");
const email = ref("");
const password = ref("");

const isLoadingStore = useIsLoadingStore();
const router = useRouter();
</script>

<template>
  <div class="flex justify-center items-center h-screen w-full">
    <div class="bg-gray-400 h-1/3 w-1/4 rounded-lg p-5">
      <h1 class="text-3xl font-bold text-center pb-3">Login</h1>
      <form>
        <UiInput
          v-model="name"
          type="name"
          class="mb-3 bg-gray-300"
          placeholder="Name"
        />
        <UiInput
          v-model="email"
          type="email"
          class="mb-3 bg-gray-300"
          placeholder="Email"
        />
        <UiInput
          v-model="password"
          type="password"
          class="mb-3 bg-gray-300"
          placeholder="Password"
        />
        <div class="flex gap-3 justify-center">
          <UiButton type="button">Login</UiButton>
          <UiButton type="button">Register</UiButton>
        </div>
      </form>
    </div>
  </div>
</template>
