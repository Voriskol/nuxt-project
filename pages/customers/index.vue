<script setup lang="ts">
import { useQuery } from "@tanstack/vue-query";
import { COLLECTION_CUSTOMERS, DB_ID } from "~/app.constants";
import type { ICustomer } from "~/types/deals.types";

useHead({
  title: "Customers",
});

const { data, isLoading } = useQuery({
  queryKey: ["customers"],
  queryFn: () =>
    DB.listDocuments(DB_ID, COLLECTION_CUSTOMERS) as unknown as ICustomer[],
});

const customers = data?.value?.documents as unknown as ICustomer[];
</script>

<template>
  <div class="p-10 text-black">
    <h1 class="text-3xl font-bold text-black">Our clients</h1>
    <div v-if="isLoading">Loading...</div>
    <UiTable v-else>
      <UiTableHeader>
        <UiTableRow>
          <UiTableHead class="w-[200px]">Name</UiTableHead>
          <UiTableHead class="w-[200px]">Email</UiTableHead>
          <UiTableHead>Source</UiTableHead>
        </UiTableRow>
      </UiTableHeader>
      <UiTableBody>
        <UiTableRow v-for="customer in customers" :key="customer.$id">
          <UiTableCell class="font-medium">
            {{ customer.name }}
          </UiTableCell>
          <UiTableCell>
            {{ customer.email }}
          </UiTableCell>
          <UiTableCell v-if="customer.from_source">
            {{ customer.from_source }}
          </UiTableCell>
          <UiTableCell v-else>No source</UiTableCell>
        </UiTableRow>
      </UiTableBody>
    </UiTable>
  </div>
</template>
