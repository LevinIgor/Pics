<template>
  <header>
    <div @click="$router.push({ name: 'main' })" class="logo">Cute Logo</div>
    <ul>
      <li @click="$router.push({ name: 'main' })">Main</li>
      <li @click="$router.push({ name: 'account' })">Account</li>
    </ul>
  </header>
</template>

<script setup></script>

<style lang="scss" scoped>
  header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: sticky;
    top: 0;
    z-index: 10000000;
    background-color: var(--color-background);
    user-select: none;
    padding: 1rem;
  }
  ul {
    display: flex;
    gap: 1rem;
  }
  li {
    box-sizing: border-box;
    list-style: none;
    padding: 0.5rem;
    cursor: pointer;
    border-bottom: 1px solid transparent;
    transition: all 0.2s ease-in-out;

    &:hover {
      color: rgba(255, 255, 255, 0.842);
      border-color: rgba(255, 91, 91, 0.77);
    }
  }
  .logo {
    font-size: 1.5rem;
    color: pink;
  }
</style>
