<script setup lang="ts">
  import axios from 'axios';
  import { ref } from 'vue';

  const yesAnswer = ref(false);

  // Function to handle "Yes" button click
  const handleYes = () => {
    yesAnswer.value = true;
  };

  // Function to close the list
  const closeList = () => {
    yesAnswer.value = false;
  };

  const nasaImg = ref<string | null>(null);

  const nasaKey = import.meta.env.VITE_NASA_KEY;

  const fetchNasaImage = async () => {
  try {
    const response = await axios.get(`https://api.nasa.gov/planetary/apod?api_key=${nasaKey}`);
    nasaImg.value = response.data.url;
  } catch (error) {
    console.error('Error fetching NASA image:', error);
  }
};

fetchNasaImage();
</script>

<template>
    <div class="NasaImgWrapper">
      <button v-if="!yesAnswer" @click="handleYes">View NASA Image</button>
      <button v-else @click="closeList">Close</button>
    </div>

    <ul v-if="yesAnswer">
      <li>
        <img :src="nasaImg" alt="NASA Astronomy Picture of the Day" v-if="nasaImg" />
        <p v-else>Loading image...</p>
      </li>
    </ul>
</template>
