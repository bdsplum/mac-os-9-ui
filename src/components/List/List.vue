<template>
    <div class="list">
        <slot />
    </div>
</template>

<script setup>

</script>

<style lang="scss" scoped>
    @import "../../styles/colours";

    .list {
        border: 1px solid black;
        width: fit-content;
        min-width: 150px;
        background-color: $grey-1;
        box-shadow: 1px 1px $grey-10, inset 1px 1px white, inset -1px -1px $grey-8;
        display: flex;
        flex-direction: column;
    }
</style>