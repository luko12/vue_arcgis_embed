<script setup lang="ts">
import WebMap from '../components/WebMap.vue'
</script>

<template>
  <div class="map">
    <WebMap msg="06ca49d0ddb447e7817cfc343ca30df9" />
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .map {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
