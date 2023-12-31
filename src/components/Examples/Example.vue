<template>
    <div class="example">
        <slot name="component"/>
    </div>
    <div class="docs">
        <StickyNote
            width="200"
            height="150"
            theme="red"
            class="docs--title"
        >
            {{ name }}
        </StickyNote>
        <StickyNote
            width="200"
            theme="green"
            class="docs--info"
        >
            <slot name="docs" />
        </StickyNote>
    </div>
</template>

<script setup>
    import StickyNote from '../StickyNote.vue';

    const props = defineProps({
        name: String
    });
</script>

<style lang="scss" scoped>
    .docs {
        position: relative;

        &--title {
            font-family: helvetica;
            font-size: 16px;
            font-weight: bold;
            text-transform: uppercase;
        }

        &--info {
            position: absolute;
            top: 50px;
            left: 40px;

            &:deep(ul) {
                padding-inline-start: 20px;
            }

            &:deep(li) {
                list-style-type: square;
            }
        }
    }
</style>