<template>
  <NotionRenderer :blockMap="blockMap" fullPage />
</template>

<script setup>
import { getPageBlocks, NotionRenderer } from "vue-notion";
import { ref } from "vue";

const blockMap = ref(null);

const props = defineProps({
  id: {
    required: true,
    type: String,
  },
});

getPageBlocks(props.id).then((value) => (blockMap.value = value));
</script>

<style>
/* optional Notion-like styles */
@import "vue-notion/src/styles.css";

.notion-page-offset {
  margin-top: 0px;
}

.notion-title {
  color: #e39;
}
</style>
