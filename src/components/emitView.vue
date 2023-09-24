<script setup>
import { ref } from 'vue';

</script>



<template>
    <button @click="$emit('increaseBy', 1)">
    Increase by 1
    </button>
</template>
