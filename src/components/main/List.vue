<template>
  <ul>
    <li
      v-for="post of filteredList"
      :key="post.id"
      @click="
        $emit('changeId', post.id);
        updateName('Post');
      "
    >
      <span>{{ post.title }}</span>
      <span :class="post.category.toLowerCase()">{{ post.category }}</span>
    </li>
  </ul>
</template>
<script setup>
import { getPageTable } from "vue-notion";
import { ref, computed, inject } from "vue";

const { updateName } = inject("name");
const { category } = inject("category");

const list = ref([]);

//비동기 함수, promise 반환
getPageTable("9ca69489899649d9a5d681448a9608d6").then((value) => {
  list.value = value;
});
const keyword = inject("keyword");
const filteredList = computed(() => {
  return list.value.filter((item) => {
    return (
      (item.category == category.value || category.value == "") &&
      item.title.includes(keyword.value)
    );
  });
});
</script>

<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}
li {
  border-bottom: 1px solid black;
  padding: 10px;
  display: flex;
  color: #e39;
  font-weight: bold;
}
li:hover {
  background-color: #e39;
  color: white;
  cursor: pointer;
  transition: 0.7s;
}

li span:nth-child(2) {
  margin-left: auto;
  border-radius: 5px;
  padding: 2px 5px;
}

li span:nth-child(2).motivation {
  background-color: lightblue;
}
li span:nth-child(2).save {
  background-color: lightgoldenrodyellow;
}
</style>
