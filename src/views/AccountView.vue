<template>
  <div class="account mt-5">
    <div class="d-flex gap-4">
      <img
        src="https://images.pexels.com/photos/3571576/pexels-photo-3571576.jpeg?auto=compress&cs=tinysrgb&w=1600"
        alt="avatar"
        class="avatar mr-3"
      />
      <div>
        <div class="account_name">Account Name</div>
        <div class="actions mt-4">
          <button
            v-if="isFollowing"
            @click="isFollowing = false"
            class="btn_unsubscribe"
          >
            Unsubscribe
          </button>
          <button v-else @click="isFollowing = true" class="btn_subscribe">
            Follow
          </button>
        </div>
      </div>
    </div>
    <div class="d-flex mt-3 gap-4">
      <span class="d-flex"><b>99</b> Following</span>
      <div class="d-flex"><b>999</b> Followers</div>
      <div class="d-flex"><b>9999</b> Likes</div>
    </div>
    <p class="mt-3">
      Lorem ipsum dolor sit, amet consectetur adipisicing elit. Optio,
      inventore!
    </p>
    <p class="link d-flex align-items-start">
      <i class="bi bi-link-45deg" />
      <a href="https://www.youtube.com/watch?v=dQw4w9WgXcQ" target="_blank">
        https://www.youtube.com/watch?v=dQw4w9WgXcQ</a
      >
    </p>
    <div class="tabs d-flex w-100 mt-5">
      <div
        class="bottom_line"
        :style="{
          left:
            currentTab === 'Collections'
              ? '0px'
              : currentTab === 'Saved'
              ? '150px'
              : '300px',
        }"
      />
      <div
        @click="currentTab = 'Collections'"
        class="tab"
        :class="{ tab_active: currentTab === 'Collections' }"
      >
        <div class="tab_name">Collections</div>
      </div>
      <div
        @click="currentTab = 'Saved'"
        class="tab"
        :class="{ tab_active: currentTab === 'Saved' }"
      >
        <div class="tab_name">Saved</div>
      </div>
      <div
        @click="currentTab = 'All'"
        class="tab"
        :class="{ tab_active: currentTab === 'All' }"
      >
        <div class="tab_name">All</div>
      </div>
    </div>
    <div class="tab_content w-100">
      <div
        v-if="currentTab === 'Collections'"
        class="tab_content_item collections"
      >
        <div class="collection">
          <img
            class="collection_img"
            src="https://images.pexels.com/photos/1428277/pexels-photo-1428277.jpeg?auto=compress&cs=tinysrgb&w=1600"
            alt=""
          />
          <span class="collection_name">Collection 1</span>
        </div>
        <div class="collection">
          <img
            class="collection_img"
            src="https://images.pexels.com/photos/33109/fall-autumn-red-season.jpg?auto=compress&cs=tinysrgb&w=1600"
            alt=""
          />
          <span class="collection_name">Collection 2</span>
        </div>
        <div class="collection">
          <img
            class="collection_img"
            src="https://images.pexels.com/photos/709552/pexels-photo-709552.jpeg?auto=compress&cs=tinysrgb&w=1600"
            alt=""
          />
          <span class="collection_name">Collection 3</span>
        </div>
        <div class="collection">
          <img
            class="collection_img"
            src="https://images.pexels.com/photos/326055/pexels-photo-326055.jpeg?auto=compress&cs=tinysrgb&w=1600"
            alt=""
          />
          <span class="collection_name">Collection 4</span>
        </div>
        <div class="collection">
          <img
            class="collection_img"
            src="https://images.pexels.com/photos/459203/pexels-photo-459203.jpeg?auto=compress&cs=tinysrgb&w=1600"
            alt=""
          />
          <span class="collection_name">Collection 5</span>
        </div>
      </div>
      <div v-if="currentTab === 'Saved'" class="tab_content_item">
        <InfinityTape :imgs="imgs" />
      </div>
      <div v-if="currentTab === 'All'" class="tab_content_item">
        <InfinityTape :imgs="imgs2" />
      </div>
    </div>
  </div>
</template>

<script setup>
  import { ref } from "vue";
  import InfinityTape from "@/components/InfinityTape.vue";
  import imgs from "@/store/imgs.json";
  import imgs2 from "@/store/imgs2.json";

  const currentTab = ref("Collections");

  const isFollowing = ref(false);
</script>

<style lang="scss" scoped>
  b {
    padding-right: 0.4rem;
  }

  .link {
    cursor: pointer;
    &:hover {
      text-decoration: underline;
    }
    a {
      margin-left: 0.3rem;
    }
  }
  .avatar {
    box-sizing: border-box;
    width: 116px;
    height: 116px;
    border-radius: 50%;
    object-fit: cover;
    object-position: center;
    border: 1px solid black;
    box-shadow: 0 0 10px black;
    transition: all 0.3s ease-in-out;
    cursor: pointer;
  }

  .tabs {
    background-color: var(--color-background-soft);
    border-radius: 1rem 1rem 0 0;
    border: 1px solid var(--color-border);
    border-bottom: none;
    overflow: hidden;
    user-select: none;

    .bottom_line {
      width: 150px;
      height: 3px;
      background-color: rgba(220, 47, 47, 0.452);
      transition: all 0.2s cubic-bezier(0.55, 0.055, 0.675, 0.19);
      position: absolute;
      bottom: 0;
      left: 0;
      z-index: 10000;
    }
  }

  .tab {
    padding: 0.5rem 2rem;
    cursor: pointer;
    width: 150px;
    text-align: center;
  }

  .tab_active {
    transition: all 0.3s ease-in-out;
    z-index: 100;
    background-color: var(--color-background-mute);
  }

  .tab_content {
    background-color: var(--color-background-mute);
    min-height: 100vh;
    border: 1px solid var(--color-border);
  }

  .collections {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));

    padding: 1rem;
    .collection {
      position: relative;
      display: flex;
      flex-direction: column;

      background-color: var(--color-background-soft);

      box-shadow: 0 0 2px var(--color-border);
      overflow: hidden;

      cursor: pointer;
      &_img {
        object-fit: cover;
        object-position: center;
        width: 100%;
        height: 100%;
      }
      &_name {
        position: absolute;
        width: 100%;
        height: 100%;
        top: 0;
        left: 0;

        font-size: 1.3rem;
        font-weight: bold;
        display: flex;
        align-items: center;
        justify-content: center;
        padding-top: 0.8rem;
        background-color: rgba(0, 0, 0, 0.392);
        backdrop-filter: blur(2px);
        transition: backdrop-filter 0.3s ease-in-out;
      }

      &:hover {
        .collection_name {
          backdrop-filter: blur(0);
          transform: translateY(80%);
          background-color: rgba(0, 0, 0, 0.554);
          display: flex;
          align-items: start;
          transition: transform 0.1s linear;
        }
      }
    }
  }

  .btn_subscribe {
    background-color: rgba(220, 47, 47, 0.382);
    padding: 0.2rem 3rem;
    border: none;
    border-radius: 0.3rem;
    color: var(--color-text);
    transition: background-color 0.3s;

    &:hover {
      background-color: rgba(220, 47, 47, 0.467);
    }
  }

  .btn_unsubscribe {
    background-color: rgba(134, 134, 134, 0.382);
    padding: 0.2rem 3rem;
    border: none;
    border-radius: 0.3rem;
    color: var(--color-text);
    transition: background-color 0.3s;
  }

  .account_name {
    font-size: 1.5rem;
  }
</style>
