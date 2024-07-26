<script setup lang="ts">
import { storage } from "@/utils/appwrite";
import { useMutation, useQuery } from "@tanstack/vue-query";
import { v4 as uuidv4 } from "uuid";
import { COLLECTION_CUSTOMERS, DB_ID, STORAGE_ID } from "~/app.constants";
import type { ICustomer } from "~/types/deals.types";

interface ICustomerformState
  extends Pick<ICustomer, "avatar_url" | "email" | "name" | "from_source"> {}

useHead({
  title: "Client edit",
});

const route = useRoute();
const customerId = route.params.id as string;

const { handleSubmit, defineField, setFieldValue, setValues, values } =
  useForm<ICustomerformState>({
    initialValues: {
      avatar_url: "",
      email: "",
      name: "",
      from_source: "",
    },
  });
</script>

<template></template>
