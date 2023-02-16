<template>
  <div class="modal_wrapper" @click.self="emits('close')">
    <div class="image_view">
      <img :src="url" alt="" />
      <div class="info_block">
        <ul class="tags">
          <li>tag1</li>
          <li>tag2</li>
          <li>tag3</li>
          <li>tag4</li>
        </ul>
        <div class="description">Picture text name</div>
        <div class="control-block">
          <button>Save</button>
          <button @click="emits('close')">Close</button>
          <button>Share</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
  import { defineProps, defineEmits, ref } from "vue";

  const props = defineProps({
    tags: {
      type: Array,
      default: () => [],
    },
    description: {
      type: String,
      default: "",
    },
    url: {
      type: String,
      default: "",
    },
  });

  const emits = defineEmits({
    save: {
      type: Boolean,
      default: false,
    },
    close: {
      type: Boolean,
      default: false,
    },
    share: {
      type: Boolean,
      default: false,
    },
  });
</script>

<style scoped>
  img {
    width: 100%;
  }
  .modal_wrapper {
    position: fixed;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: rgba(0, 0, 0, 0.5);
  }

  .image_view {
    max-width: 1000px;
    min-width: 60%;
    max-height: 90vh;
    background-color: rgb(255, 255, 255);
    display: grid;
    grid-template-columns: 1fr 1fr; 
    min-height: 50vh;
    justify-content: center;
    align-items: center;
    padding: 1rem;
    border-radius: 1rem;
  }
  .image_view::-webkit-scrollbar {
    display: none;
  }
</style>
