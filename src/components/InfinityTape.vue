<template>
  <div class="container">
    <img
      v-for="img in imgs"
      :key="img.id"
      @click="emits('onPictureClick', img.url)"
      :src="img.url"
    />
  </div>
</template>

<script setup>
  import { defineEmits, defineProps } from "vue";

  const props = defineProps({
    imgs: {
      type: Array,
      required: true,
      default: () => [],
    },
  });

  const emits = defineEmits(["onPictureClick"]);
</script>

<style scoped>
  img {
    max-width: 100%;
    display: block;
    cursor: pointer;
    margin-bottom: 1rem;
  }

  .container {
    margin-top: 5rem;
    column-count: 4;
    column-gap: 10px;
  }
</style>
