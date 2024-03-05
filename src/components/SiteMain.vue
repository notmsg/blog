<template>
  <main>
    <!--<component :is="comp[name]" />-->
    <List
      v-if="name == 'List'"
      @change-id="
        (newId) => {
          idvalue = newId;
        }
      "
    />
    <Post v-if="name == 'Post'" :id="idvalue" />
  </main>
</template>

<script setup>
import { ref, defineAsyncComponent, onMounted, inject } from "vue";

const idvalue = ref("91caab9a9bc945309802175ab9f7d32d");

const List = defineAsyncComponent(() => import("@/components/main/List.vue"));
const Post = defineAsyncComponent(() => import("@/components/main/Post.vue"));

const comp = { List, Post };

const { name } = inject("name");
</script>

<style scoped>
main {
  width: 80%;
  margin: 10px auto;
}
</style>
