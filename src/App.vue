<script setup>
    import ScrollContainer from './components/Scroll/ScrollContainer.vue';
</script>

<template>
    <ScrollContainer>
        <div class="body">
            <div>Hello!</div>
            <div>Hello!</div>
            <div>Hello!</div>
            <div>Hello!</div>
            <div>Hello!</div>
            <div>Hello!</div>
            <div>Hello!</div>
            <div>Hello!</div>
        </div>
    </ScrollContainer>
</template>

<style scoped lang="scss">
    .body {
        &> div {
            margin-bottom: 100px;
        }
    }
</style>
