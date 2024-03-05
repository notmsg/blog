<template>
  <div class="search">
    <input
      placeholder="Search"
      :value="keyword"
      @input="
        if (keywordModifiers?.upper) {
          $emit('update:keyword', $event.target.value.toUpperCase());
        } else {
          $emit('update:keyword', $event.target.value);
        }
      "
    />
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

defineProps(["keyword", "keywordModifiers"]);
defineEmits(["update:keyword"]);
</script>
<style></style>
