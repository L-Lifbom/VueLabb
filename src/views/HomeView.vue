<script setup lang="ts">
import { ref, computed, onMounted } from 'vue';
import NasaImg from '@/components/NasaImg.vue';
import FormsItem from '@/components/FormsItem.vue';
import ArrayItem from '@/components/ArrayItem.vue';

const currentTime = ref(new Date());

setInterval(() => {
  currentTime.value = new Date();
}, 1000);

const greeting = computed(() => {
  const hour = currentTime.value.getHours();
  if (hour >= 6 && hour < 12) {
    return "morning";
  } else if (hour >= 12 && hour < 17) {
    return "afternoon";
  } else if (hour >= 17 && hour < 22) { 
    return "evening";
  } else {
    return "night";
  }
});

const message = computed(() => `Good ${greeting.value}!`);

const userInput = ref<string>('');

onMounted(() => {
  console.log('Component is mounted!');
});
</script>

<template>
  <section class="homeWrapper">
    <h1>{{ message }}</h1>
    <h3>Welcome to my Nasa inspired app!</h3>
    <NasaImg />
    <input type="text" v-model="userInput" placeholder="Write something" />
    <FormsItem :userInput="userInput"/>
    <ArrayItem />
  </section>
</template>

<style scoped>
.homeWrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
