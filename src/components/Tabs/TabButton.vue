<template>
    <div 
        class="tab-button"
        :class="{ 'tab-button--active': active }"
        @click="emits('click')"
    >
        <slot />
    </div>
</template>

<script setup>
    const props = defineProps({
        /**
         * Whether the tab is active
         */
        active: Boolean
    });

    const emits = defineEmits(['click']);
</script>

<style lang="scss" scoped>
    @import "../../styles/colours";

    .tab-button {
        position: relative;
        padding: 2px 16px;
        overflow: hidden;
        font-size: 14px;
        cursor: pointer;

        &::before, &::after {
            content:"";
            position:absolute;
            top:0; 
            width:50%; 
            height:100%;
            background-color: $grey-3;
            z-index:-1;    
            transform-origin:100% 100%;
            border: 1px solid black;
        }

        &:after {
            right: -1px;
            border-top-right-radius: 6px;
            transform: skewX(20deg);
            border-left: none;
            box-shadow: inset 0 1px white, inset -1px 0 $grey-1;
        }

        &::before {
            left: -1px;
            border-top-left-radius: 6px;
            transform: skewX(-20deg);
            box-shadow: inset 1px 1px white;
        }

        &--active {
            border-bottom: 1px solid $grey-2;
            box-shadow: 0 1px $grey-2;

            &::before, &::after {
                background-color: $grey-2;
            }

            &::before {
                box-shadow: inset 1px 1px white;
            }

            &::after {
                box-shadow: inset 0 1px white, inset -1px 0 $grey-3;
            }
        }

        &:hover {
            &::before, &::after {
                background-color: #666666;
                color: white;
            }

            &::before {
                box-shadow: inset 1px 1px #434343;
            }

            &::after {
                box-shadow: inset 0 1px #434343, inset -1px 0 $grey-6;
            }
        }
    }

</style>