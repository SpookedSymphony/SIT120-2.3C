<script setup>
import { ref, reactive, computed, watch } from 'vue'

const items = ref([{ message: 'Milk' }, { message: 'Bread' }])
</script>

<template>
    <ul>
        <template v-for="item in itemList"> 
            <li>{{ item.message }}</li>
        </template>
    </ul>
</template>
    


