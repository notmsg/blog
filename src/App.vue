<template>
  <SiteHeader />
  <SiteMain />
  <div class="my-loader" v-show="loading">
    <Loading />
  </div>
  <SiteFooter />
</template>

<script setup>
import { ref, onMounted, provide } from "vue";
import SiteHeader from "./components/SiteHeader.vue";
import SiteMain from "./components/SiteMain.vue";
import SiteFooter from "./components/SiteFooter.vue";
import Loading from "@/components/Loading.vue";

const loading = ref(true);
const name = ref("List");
const category = ref("");
const keyword = ref("");

provide("name", {
  name,
  updateName(newName) {
    name.value = newName;
  },
});

provide("category", {
  category,
  updateCategory(newCategory) {
    category.value = newCategory;
  },
});

provide("keyword", keyword);
/*
const changeCategory = function (newCate) {
  name.value = "List";
  category.value = newCate;
};
*/
onMounted(() => {
  setTimeout(() => {
    loading.value = false;
  }, 2000);
});
</script>

<style>
.my-loader {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.3);

  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
