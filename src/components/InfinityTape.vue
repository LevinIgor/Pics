<template>
  <div class="container">
    <img
      v-for="img in imgs"
      :key="img.id"
      @click="openedImage ? (selectedImage = img) : null"
      :src="img.url"
    />
  </div>
  <ImageView
    v-if="selectedImage"
    :url="selectedImage.url"
    @close="selectedImage = null"
  />
</template>

<script setup>
  import { defineProps, ref } from "vue";
  import ImageView from "@/components/ImageView.vue";

  const props = defineProps({
    imgs: {
      type: Array,
      required: true,
      default: () => [],
    },
    openedImage: {
      type: Boolean,
      default: true,
    },
  });

  const selectedImage = ref(null);
</script>

<style scoped>
  img {
    max-width: 100%;
    display: block;
    cursor: pointer;
    margin-bottom: 1rem;
  }

  .container {
    column-count: 4;
    column-gap: 10px;
  }
</style>
