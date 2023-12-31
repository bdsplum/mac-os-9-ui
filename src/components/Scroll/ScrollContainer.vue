<template>
    <div class="scroll">
        <div class="scroll__upper">
            <div 
                ref="content"
                class="scroll__content"
                @mousewheel.stop.passive="mousewheel"
            >
                <slot />
            </div>
            <ScrollBar 
                class="scroll__bar--upper" 
                vertical 
                :scroll-max="scrollHeight"
                :visible-max="height"
                :current="scrollTop"
                @scroll="scrollTo(undefined, $event)"
            />
        </div>
        <div class="scroll__lower">
            <ScrollBar 
                class="scroll__bar--lower" 
                horizontal
                :scroll-max="scrollWidth"
                :visible-max="width"
                :current="scrollLeft"
                @scroll="scrollTo($event)"
            />
            <div class="scroll__corner">
                <div class="scroll__corner-handle"></div>
            </div>
        </div>
    </div>
</template>

<script setup>
    import ScrollBar from './ScrollBar.vue';
    import { ref, onMounted, onUnmounted } from 'vue';
    import { useResizeObserver } from '@vueuse/core';

    const content = ref(null);
    const scrollHeight = ref(0);
    const scrollWidth = ref(0);
    const height = ref(0);
    const width = ref(0);
    const scrollTop = ref(0);
    const scrollLeft = ref(0);

    const { stop } = useResizeObserver(content, () => {
        updateSizes();
    });

    onMounted(() => {
        if(content?.value) {
            updateSizes();
        }
    });

    onUnmounted(() => {
        if(stop) {
            stop();
        }
    });

    /**
     * Updates the content scroll info
     */
    function updateSizes() {
        scrollHeight.value = content.value?.scrollHeight;
        height.value = content.value?.clientHeight;
        scrollWidth.value = content.value?.scrollWidth;
        width.value = content.value?.clientWidth;
        scrollTop.value = content.value?.scrollTop;
        scrollLeft.value = content.value?.scrollLeft;
    }

    /**
     * Handles the content mouse wheel event
     * @param {Event} e - the mouse wheel event
     */
    function mousewheel(e) {
        // todo: conditional stop propagation if there is nothing to scroll?

        if(!content?.value) {
            return;
        }

        scrollTo(content?.value.scrollLeft + e.deltaX, content?.value.scrollTop + e.deltaY);
    }

    /**
     * Scrolls the content to a given position
     * @param {Number} x - the left scroll coordinate
     * @param {Number} y - the top scroll coordinate
     */
    function scrollTo(x = scrollLeft.value, y = scrollTop.value) {
        if(!content?.value) {
            return;
        }

        content.value.scrollTo(x, y);
        updateSizes();
    }
</script>

<style lang="scss" scoped>
    @import "../../styles/colours";

    .scroll {
        height: 100%;
        width: 100%;
        display: flex;
        flex-direction: column;

        &__content {
            flex: 1 1 auto;
            overflow: hidden;
            overscroll-behavior: none;
        }

        &__upper {
            display: flex;
            flex: 1 1 auto;
            overflow: hidden;
        }

        &__lower {
            display: flex;
            flex: 0 0 auto;
        }

        &__bar {
            &--upper {
                flex: 0 0 auto;
                border-bottom: none;
            }

            &--lower {
                flex: 1;
                border-right: none;
            }
        }

        &__corner {
            border: 1px solid;
            border-color: black transparent transparent black;
            width: 16px;
            height: 16px;
            flex: 0 0 auto;
            background-color: $grey-3;
            display: flex;
            justify-content: center;
            align-items: center;
            box-shadow: inset 1px 1px white;

            &-handle {
                width: 8px;
                height: 1px;
                transform: rotate(135deg);
                background-color: $grey-5;
                box-shadow: 0px 3px white, 0px 2px $grey-5, 0px 1px white, 0px -1px white, 0px -2px $grey-5;
            }
        }
    }
</style>