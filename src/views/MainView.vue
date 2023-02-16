<script setup>
  import InfinityTape from "@/components/InfinityTape.vue";
  import ImageView from "@/components/ImageView.vue";

  import { ref } from "vue";

  const isPictureShowing = ref(false);
  const pictureUrl = ref("");

  function onPictureClick(e) {
    isPictureShowing.value = true;
    pictureUrl.value = e;
  }

  const imgs = ref([
    {
      url: "https://assets.codepen.io/12005/windmill.jpg",
      alt: "pic1",
      tags: [
        {
          name: "tag1",
          color: "red",
        },
      ],
      description: "Nature",
    },
    {
      url: "https://images.pexels.com/photos/3573351/pexels-photo-3573351.png?auto=compress&cs=tinysrgb&w=1600",
      alt: "pic1",
      tags: [
        {
          name: "tag1",
          color: "red",
        },
      ],
      description: "Nature",
    },
    {
      url: "https://images.pexels.com/photos/3617500/pexels-photo-3617500.jpeg?auto=compress&cs=tinysrgb&w=1600",
      alt: "pic1",
      tags: [
        {
          name: "tag1",
          color: "red",
        },
      ],
      description: "Nature",
    },
    {
      url: "https://images.pexels.com/photos/2754200/pexels-photo-2754200.jpeg?auto=compress&cs=tinysrgb&w=1600",
      alt: "pic1",
      tags: [
        {
          name: "tag1",
          color: "red",
        },
      ],
      description: "Nature",
    },
    {
      url: "https://images.pexels.com/photos/2335126/pexels-photo-2335126.jpeg?auto=compress&cs=tinysrgb&w=1600",
      alt: "pic1",
      tags: [
        {
          name: "tag1",
          color: "red",
        },
      ],
      description: "Nature",
    },
    {
      url: "https://images.pexels.com/photos/2365457/pexels-photo-2365457.jpeg?auto=compress&cs=tinysrgb&w=1600",
      alt: "pic1",
      tags: [
        {
          name: "tag1",
          color: "red",
        },
      ],
      description: "Nature",
    },
    {
      url: "https://images.pexels.com/photos/3571551/pexels-photo-3571551.jpeg?auto=compress&cs=tinysrgb&w=1600",
      alt: "pic1",
      tags: [
        {
          name: "tag1",
          color: "red",
        },
      ],
      description: "Nature",
    },
    {
      url: "https://images.pexels.com/photos/3375116/pexels-photo-3375116.jpeg?auto=compress&cs=tinysrgb&w=1600",
      alt: "pic1",
      tags: [
        {
          name: "tag1",
          color: "red",
        },
      ],
      description: "Nature",
    },
    {
      url: "https://images.pexels.com/photos/2674052/pexels-photo-2674052.jpeg?auto=compress&cs=tinysrgb&w=1600",
      alt: "pic1",
      tags: [
        {
          name: "tag1",
          color: "red",
        },
      ],
      description: "Nature",
    },
    {
      url: "https://images.pexels.com/photos/3181458/pexels-photo-3181458.jpeg?auto=compress&cs=tinysrgb&w=1600",
      alt: "pic1",
      tags: [
        {
          name: "tag1",
          color: "red",
        },
      ],
      description: "Nature",
    },
    {
      url: "https://images.pexels.com/photos/1144687/pexels-photo-1144687.jpeg?auto=compress&cs=tinysrgb&w=1600",
      alt: "pic1",
      tags: [
        {
          name: "tag1",
          color: "red",
        },
      ],
      description: "Nature",
    },
    {
      url: "https://images.pexels.com/photos/3512848/pexels-photo-3512848.jpeg?auto=compress&cs=tinysrgb&w=1600",
      alt: "pic1",
      tags: [
        {
          name: "tag1",
          color: "red",
        },
      ],
      description: "Nature",
    },
  ]);
</script>

<template>
  <InfinityTape @onPictureClick="onPictureClick" :imgs="imgs" />
  <ImageView
    v-if="isPictureShowing"
    @close="isPictureShowing = false"
    :url="pictureUrl"
  />
</template>

<style scoped></style>
