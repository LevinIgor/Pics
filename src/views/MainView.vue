<script setup>
  import InfinityTape from "@/components/InfinityTape.vue";
  import imgs from "@/store/imgs.json";
  import { ref } from "vue";

  const mode = ref("following");
</script>

<template>
  <div class="switcher mt=5 mb-5 text-center">
    <span @click="mode = 'following'" :class="{ active: mode === 'following' }"
      > <i class="bi bi-people-fill" />Following
      <div
        class="bottom_line"
        :style="{ left: mode === 'following' ? '0px' : '100px' }"
    /></span>
    <span @click="mode = 'for you'" :class="{ active: mode === 'for you' }"
      ><i class="bi bi-house-door-fill" />For you</span
    >
  </div>
  <InfinityTape :imgs="imgs" />
</template>

<style lang="scss" scoped>

  .switcher {
    i{
      margin-right: .5rem;
    }
    position: relative;
    span {
      display: inline-block;
      cursor: pointer;
      width: 100px;
      text-align: center;
      white-space: nowrap;
    }
    .active {
      color: rgba(255, 255, 255, 0.847);
    }

    .bottom_line {
      position: absolute;
      bottom: -5px;
      left: 0;
      height: 1px;
      width: 100px;
      background-color: rgba(255, 91, 91, 0.77);
      z-index: 10;
      transition: all 0.3s ease-in-out;
    }
  }
</style>
