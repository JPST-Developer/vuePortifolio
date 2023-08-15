<script setup>
import stickyHeader from './components/stickHeader.vue'
import mainComponent from './components/mainComponent.vue'
</script>

<template>
  <div class="container">
    <sticky-header />
    <main-component />
  </div>
</template>

<style scoped>
.container {
  display: flex;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 6rem;
  padding-right: 6rem;
  margin-left: auto;
  margin-right: auto;
  gap: 1rem;
  justify-content: space-between;
}
</style>
