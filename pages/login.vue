<script setup lang="ts">
import { v4 as uuid } from "uuid";
useHead({
  title: "Login",
});

const name = ref("");
const email = ref("");
const password = ref("");

const isLoadingStore = useIsLoadingStore();
const authStore = useAuthStore();
const router = useRouter();

const login = async () => {
  isLoadingStore.set(true);
  await account.createEmailPasswordSession(email.value, password.value);
  const response = await account.get();
  if (response) {
    authStore.set({
      name: response.name,
      email: response.email,
      status: response.status,
    });
  }
  name.value = "";
  email.value = "";
  password.value = "";

  await router.push("/");
  isLoadingStore.set(false);
};

const register = async () => {
  await account.create(uuid(), email.value, password.value, name.value);
  await login();
};
</script>

<template>
  <div class="flex justify-center items-center h-screen w-full">
    <div class="bg-gray-400 h-1/3 w-1/4 rounded-lg p-5">
      <h1 class="text-3xl font-bold text-center pb-3 text-black">Login</h1>
      <form class="text-black">
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
          <UiButton class="cursor-pointer" @click="login" type="button"
            >Login</UiButton
          >
          <UiButton class="cursor-pointer" @click="register" type="button"
            >Register</UiButton
          >
        </div>
      </form>
    </div>
  </div>
</template>
