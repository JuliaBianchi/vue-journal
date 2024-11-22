<script lang="ts" setup>
import { userInjectionKey  } from "@/InjectionKeys";
import DateDisplay from "./DateDisplay.vue";
import UseEmojis from "@/composables/UseEmojis";
import type Entry from "@/types/Entry";
import { inject } from "vue";

const { findEmoji } = UseEmojis();

const user = inject(userInjectionKey);

const props = defineProps<{
  entry: Entry;
}>();

</script>

<template>

  <div class="entry-card">

    <div class="entry-card-body">
      <component width="75" :is="findEmoji(entry.emoji)"></component>
      <div class="entry-text">{{ entry.body }}</div>
    </div>

    <div class="entry-footer">
      <DateDisplay :date="entry.createdAt" class="mr-2" />
      |
      <span class="ml-2">{{ user?.username || 'anonymous' }}</span>

    </div>

  </div>

</template>
