<script setup>
import { ref } from 'vue';

const { things } = defineProps(['things']);
</script>

<template>
  <div>
    <h1>My Child Component</h1>
    <ul>
      <li v-for="(thing, index) in things" :key="index">
        <h3>{{ thing.name }}</h3>
      </li>
    </ul>
  </div>
</template>
