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
            <div class="card__button">
                <div class="card__button-expand-decoration"></div>
            </div>            
            <div class="card__button card__button--minimise">
                <div class="card__button-minimise-decoration"></div>
            </div>
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
        height: [Number, String],
        /**
         * Optional card width
         */
        width: [Number, String]
    });
</script>

<style lang="scss" scoped>
    @import "../styles/colours";

    .card {
        border: 1px solid black;
        padding: 0 5px 5px;
        background-color: $grey-3;
        box-shadow: inset 1px 1px white, inset -1px -1px $grey-8;
        display: flex;
        flex-direction: column;
        box-sizing: border-box;

        &__header {
            height: 22px;
            display: flex;
            align-items: center;
            gap: 3px;
            font-size: 14px;
        }

        &__button {
            height: 9px;
            width: 9px;
            border: 1px solid black;
            box-shadow: inset 1px 1px $grey-3, inset -1px -1px $grey-6, -1px -1px $grey-6, 1px 1px white;
            background: rgb(2,0,36);
            background: linear-gradient(135deg, rgba(2,0,36,1) 0%, rgba(153,153,153,1) 0%, rgba(255,255,255,1) 100%);
            display: flex;

            &--minimise {
                align-items: center;
            }

            &-minimise-decoration {
                width: 100%;
                border-top: 1px solid black;
                border-bottom: 1px solid black;
                height: 1px;
            }

            &-expand-decoration {
                width: 55%;
                height: 55%;
                border-right: 1px solid black;
                border-bottom: 1px solid black;
            }
        }

        &__spacer {
            flex: 1 1 auto;
            height: 1px;
            background-color: $grey-5;
            margin-bottom: 1px;
            box-shadow: -1px -5px white, 0px -4px $grey-5, -1px -3px white, 0px -2px $grey-5, -1px -1px white, -1px 1px white, 0px 2px $grey-5, -1px 3px white, 0px 4px $grey-5, -1px 5px white, 0px 6px $grey-5;
        }

        &__subheader {
            height: 22px;
            background-color: $grey-1;
            display: flex;
            justify-content: center;
            align-items: center;
            border: 1px solid black;
            border-bottom: none;
            font-size: 12px;
            box-shadow: inset 1px 1px white, inset -1px -1px $grey-4, -1px 0 $grey-8, 0 -1px $grey-8, 1px 0 white;
            font-family: 'Oswald', sans-serif;
            letter-spacing: 1px;
        }

        &__scroll {
            flex: 1;
            box-shadow: -1px 0 $grey-8;

            &:deep(.scroll__content) {
                border-left: 1px solid black;
                border-top: 1px solid black;
                background-color: white;
            }

            &:deep(.scroll__bar--lower) {
                box-shadow: 0 1px white;
            }

            &:deep(.scroll__upper) {
                box-shadow: 1px 0 white;
            }
        }
        
        &__content {
            padding: 6px;
            font-size: 12px;
        }
    }
</style>