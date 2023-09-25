<script setup>
import { ref, reactive, computed, watch } from 'vue'
const cart = reactive({
    id: 1, name: 'Milk' ,
    id: 2, name: 'Bread' ,
    id: 3, name: 'Apples' ,
});
</script>

<template v-for="item in cart">
    <ul>
        <li v-if="item !== 'Yes'"> 
            <p>{{ item }}</p>
       </li>
    </ul>
</template>      