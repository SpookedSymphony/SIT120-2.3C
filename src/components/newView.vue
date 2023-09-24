<style scoped>

.cool-button {
    color: magenta;
    background: linear-gradient(95deg, green 30%, purple);
    padding: 10px;
    margin: 5px;
    cursor: pointer;
}

</style>

<template>
    <main>
        <button class="cool-button">
            <slot/>
        </button>
    </main>
</template>