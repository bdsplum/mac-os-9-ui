<script setup>
    import ScrollContainer from './components/Scroll/ScrollContainer.vue';
    import WindowExample from './components/Examples/WindowExample.vue';
    import StickyExample from './components/Examples/StickyExample.vue';
    import ProgressExample from './components/Examples/ProgressExample.vue';
</script>

<template>
    <ScrollContainer>
        <div class="content">
            <WindowExample />
            <StickyExample />
            <ProgressExample />
        </div>
    </ScrollContainer>
</template>

<style scoped lang="scss">
    .content {
        display: grid;
        grid-template-columns: 700px 250px;
        justify-content: center;
        padding: 20px;
        column-gap: 20px;
        row-gap: 60px;
    }
</style>
