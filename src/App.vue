<script setup>
    import ScrollContainer from './components/Scroll/ScrollContainer.vue';
    import WindowExample from './components/Examples/WindowExample.vue';
    import StickyExample from './components/Examples/StickyExample.vue';
</script>

<template>
    <ScrollContainer>
        <div class="content">
            <WindowExample />
            <StickyExample />
        </div>
    </ScrollContainer>
</template>

<style scoped lang="scss">
    .content {
        display: grid;
        grid-template-columns: 700px 250px;
        justify-content: center;
        padding: 20px;
        gap: 20px;
    }
</style>
