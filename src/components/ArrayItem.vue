<script setup lang="ts">
  import { ref } from 'vue';

  const ArrayItems = ref<{ id: number; name: string }[]>([
    { id: 1, name: 'Item 1' },
    { id: 2, name: 'Item 2' },
    { id: 3, name: 'Item 3' },
    { id: 4, name: 'Item 4' },
    { id: 5, name: 'Item 5' },
  ]);

  const listYes = ref(false);

  const viewList = () => {
    listYes.value = true;
  };

  const closeList = () => {
    listYes.value = false;
  };

</script>

<template>
  <h1>Array</h1>
  <button v-if="!listYes" @click="viewList">View List</button>
  <button v-else @click="closeList">Close</button>
  <ul  v-if="listYes">
    <li v-for="item in ArrayItems" :key="item.id">{{ item.name }}</li>
  </ul>
</template>
z
