<template>
    <div 
        class="card"
        :style="{ height: `${height}px`, width: `${width}px` }"
    >
        <div class="card__header">
            <div class="card__button"></div>
            <div class="card__spacer"></div>
            <slot name="header" />
            <div class="card__spacer"></div>
            <div class="card__button"></div>
            <div class="card__button"></div>
        </div>
        <div class="card__subheader">
            <slot name="subheader" />
        </div>
        <ScrollContainer class="card__scroll">
            <div class="card__content">
                <slot />
            </div>
        </ScrollContainer>
    </div>
</template>

<script setup>
    import ScrollContainer from './Scroll/ScrollContainer.vue';

    const props = defineProps({
        /**
         * Optional card height
         */
        height: Number,
        /**
         * Optional card width
         */
        width: Number
    });
</script>

<style lang="scss" scoped>
    @import "../styles/colours";

    .card {
        border: 1px solid black;
        padding: 0 5px 5px;
        background-color: $grey-3;
        box-shadow: inset 1px 1px white, inset -1px -1px #999999;
        display: flex;
        flex-direction: column;

        &__header {
            height: 25px;
            display: flex;
            align-items: center;
            gap: 3px;
        }

        &__button {
            height: 20px;
            width: 20px;
            background-color: blue;
        }

        &__spacer {
            flex: 1 1 auto;
            height: 1px;
            background-color: $grey-5;
            box-shadow: -1px -5px white, 0px -4px $grey-5, -1px -3px white, 0px -2px $grey-5, -1px -1px white, -1px 1px white, 0px 2px $grey-5, -1px 3px white, 0px 4px $grey-5, -1px 5px white, 0px 6px $grey-5;
        }

        &__subheader {
            height: 25px;
            background-color: $grey-1;
            display: flex;
            justify-content: center;
            align-items: center;
            border: 1px solid black;
            border-bottom: none;
            font-size: 12px;
            box-shadow: inset 1px 1px white, inset -1px -1px $grey-4;
        }

        &__scroll {
            flex: 1;

            &:deep(.scroll__content) {
                border-left: 1px solid black;
                border-top: 1px solid black;
                background-color: white;
            }
        }
        
        &__content {
            padding: 6px;
            font-size: 12px;
        }
    }
</style>