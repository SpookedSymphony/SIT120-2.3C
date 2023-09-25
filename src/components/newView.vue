<style scoped>

.cool-button {
    color: White;
    background: linear-gradient(140deg, green 10%, purple);
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