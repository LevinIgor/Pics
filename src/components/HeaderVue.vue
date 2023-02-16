<template>
  <header>
    <div class="logo">Logo</div>
    <ul>
      <li @click="$router.push({ name: 'main' })">Main</li>
      <li @click="$router.push({ name: 'account' })">Account</li>
    </ul>
  </header>
</template>

<script setup></script>

<style scoped>
  header {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  ul {
    display: flex;
  }
  li {
    list-style: none;
  }
</style>
