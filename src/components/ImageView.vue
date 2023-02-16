<template>
  <div class="modal_wrapper" @click.self="emits('close')">
    <div class="form">
      <div class="d-flex align-items-center justify-content-between">
        <div class="author">
          <img
            src="https://images.pexels.com/users/avatars/1232402/kris-lucas-732.jpeg?auto=compress&fit=crop&h=50&w=50&dpr=1"
            alt=""
            class="avatar"
          />
          <span class="name">Author Name</span>
        </div>
        <div class="actions d-flex">
          <button class="save" @click="$emit('save')">
            <i class="bi bi-heart-fill" />Save
          </button>
          <button class="collect" @click="$emit('cancel')">
            <i class="bi bi-collection-fill" />Collect
          </button>
          <button class="close" @click="$emit('close')">
            <i class="bi bi-x" />Close
          </button>
        </div>
      </div>

      <div class="img">
        <img :src="url" alt="" />
      </div>
      <div class="control_block">
        <div class="name">Picture Name</div>
        <ul>
          <li>tag1</li>
          <li>tag2</li>
          <li>tag3</li>
        </ul>
      </div>
      <InfinityTape :imgs="imgs" :opened-image="false" />
    </div>
  </div>
</template>

<script setup>
  import { defineProps, defineEmits, ref } from "vue";
  import InfinityTape from "@/components/InfinityTape.vue";
  import imgs from "@/store/imgs3.json";

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

<style lang="scss" scoped>
  .modal_wrapper {
    position: fixed;
    overflow: scroll;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: rgba(0, 0, 0, 0.5);
    z-index: 10000000;

    &::-webkit-scrollbar {
      display: none;
    }
  }
  .form {
    max-width: 1280px;
    padding: 2rem;
    background-color: rgba(0, 0, 0, 0.955);
  }

  .img {
    position: relative;
    width: 100%;
    max-height: 1000px;
    display: flex;
    justify-content: center;
    padding-top: 4rem;

    img {
      max-width: 70%;
      max-height: 1000px;
    }
  }

  .author {
    img {
      width: 44px;
      height: 44px;
      border-radius: 50%;
    }
    .name {
      font-size: 1.5rem;
      font-weight: 600;
      margin-bottom: 1rem;
      margin-left: 1rem;
    }
  }
  .actions {
    button {
      color: var(--color-text);
      background-color: transparent;
      border: none;
      border-radius: 0.3rem;
      padding: 0.3rem 1rem;
      margin: 0 1rem;
      display: flex;
      align-items: center;
      cursor: pointer;
      user-select: none;
      i {
        margin-right: 0.3rem;
      }

      &:hover {
        background-color: rgba(240, 248, 255, 0.1);
      }
    }
  }

  .control_block {
    .name {
      margin-top: 2rem;
      font-size: 2rem;
      font-weight: 600;
      margin-left: 1rem;
    }

    ul {
      display: flex;
      gap: 1rem;
      li {
        list-style: none;
      }
      margin-bottom: 7rem;
    }
  }
</style>
