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
        display: flex;
        flex-direction: column;
        gap: 20px;
        padding: 20px;
    }
</style>
