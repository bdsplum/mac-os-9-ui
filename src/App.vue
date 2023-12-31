<script setup>
    import ScrollContainer from './components/Scroll/ScrollContainer.vue';
    import WindowExample from './components/Examples/WindowExample.vue';
    import StickyExample from './components/Examples/StickyExample.vue';
    import ProgressExample from './components/Examples/ProgressExample.vue';
    import ListExample from './components/Examples/ListExample.vue';
    import ScrollExample from './components/Examples/ScrollExample.vue';
    import Intro from './components/Examples/Intro.vue';
</script>

<template>
    <ScrollContainer>
        <Intro class="app-start" />
        <div class="content">
            <WindowExample />
            <StickyExample />
            <ListExample />
            <ProgressExample />
            <ScrollExample />
        </div>
    </ScrollContainer>
</template>

<style scoped lang="scss">
    .content {
        display: grid;
        grid-template-columns: 700px 250px;
        justify-content: center;
        padding: 30px;
        column-gap: 20px;
        row-gap: 60px;
    }

    .app-start {
        margin-top: 20px;
    }
</style>
