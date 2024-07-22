<script setup lang="ts">
import type { ICard, IColumn } from "~/components/kanban/kanban.types";
import { useKanbanQuery } from "@/components/kanban/useKanbanQuery";
import dayjs from "dayjs";
useHead({
  title: "Home",
});

const dragCard = ref<ICard | null>(null);
const sourceColumn = ref<IColumn | null>(null);

const { data, isLoading, refetch } = useKanbanQuery();
</script>

<template>
  <div class="p-10">
    <h1 class="text-3xl font-bold">My Nuxt project</h1>
    <div v-if="isLoading">One second please...</div>
    <div v-else>
      <div class="grid grid-cols-5 gap-16">
        <div
          v-for="(column, index) in data"
          :key="column.id"
          class="min-h-screen"
        >
          <div class="rounded bg-gray-400 py-1 px-5 mb-2 text-center">
            {{ column.name }}
          </div>
          <div>
            <KanbanCreateDeal :refetch="refetch" :status="column.id" />
            <UiCard
              v-for="card in column.items"
              :key="card.id"
              class="mb-3 bg-gray-300 hover:border-purple-400"
              draggable="true"
            >
              <UiCardHeader role="button"> {{ card.name }} </UiCardHeader>
              <UiCardDescription>{{ card.price }} $</UiCardDescription>
              <UiCardContent>
                <p>Компания</p>
                {{ card.companyName }}
              </UiCardContent>
              <UiCardFooter>
                {{ dayjs(card.$createdAt).format("DD MMMM YYYY") }}
              </UiCardFooter>
            </UiCard>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
