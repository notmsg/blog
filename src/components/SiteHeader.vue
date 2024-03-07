<template>
  <header>
    <img src="@/assets/topmain.jpg" />

    <nav>
      <a
        v-for="item of menu"
        :key="item"
        @click="
          updateName('List');
          updateCategory(item);
        "
        >{{ item }}</a
      >
      <div class="input-search">
        <Search v-model:keyword.upper="keyword" />
      </div>
    </nav>
  </header>
</template>

<script setup>
import Search from "./header/Search.vue";
import { inject, ref, provide } from "vue";

const { updateName } = inject("name");
const { updateCategory } = inject("category");

const menu = ["motivation", "save"];
const keyword = inject("keyword");
</script>

<style scoped>
header {
  display: flex;
  flex-direction: column;
  align-items: center;
}
img {
  width: 200px;
  transition: transform 0.7s;
}
img:hover {
  transform: scale(1.1);
}
a {
  margin: 5px;
  font-weight: bold;
  cursor: pointer;
}
nav {
  margin: 10px;
  background-color: black;
  color: white;
  width: 80%; /*헤더 크기의*/
  padding: 5px;
  border-radius: 5px;
  display: flex;
  align-items: center;
}
.input-search {
  margin-left: auto;
}
</style>
