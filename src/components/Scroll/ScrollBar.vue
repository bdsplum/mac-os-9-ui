<template>
    <div 
        class="scrollbar"
        :class="{ 'scrollbar--vertical': vertical, 'scrollbar--horizontal': horizontal, 'scrollbar--disabled': !size.visible }"
    >
        <div 
            ref="track"
            class="scrollbar__track"
        >
            <div
                v-if="size.visible"
                class="scrollbar__thumb"
                :style="{ [sizeProperty]: size.length, [offsetProperty]: size.offset }"
                @mousedown.stop="startDrag"
            >
                <div class="scrollbar__handle">
                    <div class="scrollbar__handle-line"></div>
                    <div class="scrollbar__handle-line"></div>
                    <div class="scrollbar__handle-line"></div>
                    <div class="scrollbar__handle-line"></div>
                </div>
            </div>
        </div>
        <button 
            class="scrollbar__button" 
            @click="scrollIncrement(-50)"
        >
            <div class="scrollbar__icon scrollbar__icon--prev"></div>
        </button>
        <button 
            class="scrollbar__button" 
            @click="scrollIncrement(50)"
        >
            <div class="scrollbar__icon scrollbar__icon--next"></div>
        </button>
    </div>
</template>

<script setup>
    import { onMounted, computed, ref } from 'vue';

    const props = defineProps({
        /**
         * Whether the scroll bar is vertical
         */
        vertical: Boolean,
        /**
         * Whether the scroll bar is horizontal
         */
        horizontal: Boolean,
        /**
         * The height of the scrollable area
         */
        scrollMax: Number,
        /**
         * The height of the visible area
         */
        visibleMax: Number,
        /**
         * The current scroll position
         */
        current: Number
    });

    const emit = defineEmits(['scroll']);

    const sizeProperty = computed(() => props.vertical ? 'height' : 'width');
    const offsetProperty = computed(() => props.vertical ? 'top' : 'left');

    const size = computed(() => {
        const delta = props.scrollMax - props.visibleMax;
        const pOffscreen = (delta / props.scrollMax);
        const length = (1 - pOffscreen) * 100;
        const offset = ((props.current / delta) * 100) * pOffscreen;

        return {
            visible: delta > 0,
            length: `${length}%`,
            offset: `${offset}%`
        };
    });

    /**
     * Scrolls the content a fixed increment
     * @param {Number} increment - the amount to increment the scroll by
     */
    function scrollIncrement(increment) {
        emit('scroll', props.current + increment);
    }

    const track = ref(null);

    /**
     * Sets up the thumb drag scrolling
     * @param {Event} ev - the mousedown event
     */
    function startDrag(ev) {
        const startScroll = props.current;
        const startPos = props.vertical ? ev.clientY : ev.clientX;
        const trackSize = (props.vertical ? track.value?.clientHeight : track.value?.clientWidth) * ((props.scrollMax - props.visibleMax) / props.scrollMax);

        function move(e) {
            const delta = (props.vertical ? e.clientY : e.clientX) - startPos;
            const scrollArea = props.scrollMax - props.visibleMax;
            const scrollChange = delta * ((scrollArea / trackSize));

            emit('scroll', startScroll + scrollChange);
        }

        document.addEventListener('mousemove', move);
        document.addEventListener('mouseup', () => {
            document.removeEventListener('mousemove', move);
        }, { once: true });
    }
</script>

<style lang="scss" scoped>
    @import "../../styles/colours";

    $scrollbar-inactive: $grey-2;
    $scrollbar-track: $grey-4;
    $scrollbar-thumb: $blue-1;
    $scrollbar-thumb-active: $blue-2;
    $scrollbar-text: $text;
    $scrollbar-text-inactive: $grey-6;

    $track-size: 18;
    $border-size: 1;
    $track-shadow: inset 1px 1px $grey-5, inset 2px 2px $grey-6;

    .scrollbar {
        display: flex;
        border: #{$border-size}px solid black;

        &--vertical {
            width: #{$track-size - 2*$border-size}px;
            flex-direction: column;

            .scrollbar__icon--next {
                transform: rotate(180deg);
            }

            .scrollbar__button {
                border-top: #{$border-size}px solid black;
            }

            .scrollbar__track {
                box-shadow: $track-shadow, inset -1px 0 $grey-3, inset -2px 0 $grey-7;
            }

            .scrollbar__thumb {
                top: 0;
                width: 100%;
                border-top: #{$border-size}px solid black;
                border-bottom: #{$border-size}px solid black;
            }
        }

        &--horizontal {
            height: #{$track-size - 2*$border-size}px;
            width: 100%;
            flex-direction: row;

            .scrollbar__icon--prev {
                transform: rotate(270deg);
            }

            .scrollbar__icon--next {
                transform: rotate(90deg);
            }

            .scrollbar__button {
                border-left: #{$border-size}px solid black;
            }

            .scrollbar__track {
                box-shadow: $track-shadow, inset 0 -1px $grey-3, inset 0 -2px $grey-7;
            }

            .scrollbar__thumb {
                right: 50px;
                height: 100%;
                width: 200px;
                border-right: #{$border-size}px solid black;
                border-left: #{$border-size}px solid black;
            }

            .scrollbar__handle {
                transform: rotate(270deg);
            }
        }

        &--disabled {
            .scrollbar {
                &__track, &__button {
                    background-color: $grey-2;
                    box-shadow: none;
                }

                &__button {
                    pointer-events: none;
                }

                &__icon {
                    border-bottom-color: $grey-6;
                }
            }
        }

        &__button {
            width: #{$track-size - 2*$border-size}px;
            height: #{$track-size - 2*$border-size}px;
            background-color: $grey-1;
            border: none;
            display: flex;
            justify-content: center;
            align-items: center;
            box-shadow: inset 1px 1px white, inset -1px -1px $grey-7;
            cursor: pointer;

            &:hover {
                background-color: $grey-5;
                box-shadow: inset 1px 1px #585858, inset -1px -1px $grey-8;
            }
        }

        &__icon {
            width: 0px;
            height: 0px;
            border-style: solid;
            border-width: 0 4px 4px 4px;
            border-color: transparent transparent black transparent;
        }

        &__track {
            flex: 1 1 auto;
            background-color: $scrollbar-track;
            position: relative;
        }

        &__thumb {
            position: absolute;
            background-color: $scrollbar-thumb;
            box-shadow: inset 1px 1px $blue-4, inset -1px -1px $blue-2;
            display: flex;
            align-items: center;
            justify-content: center;

            &:hover {
                background-color: $blue-2;
                box-shadow: inset 1px 1px $blue-5, inset -1px -1px $blue-3;

                .scrollbar__handle-line {
                    background-color: #9a9aff;
                    box-shadow: 0 1px #020053, 1px 1px #020053, -1px 0 #cccaff;
                }
            }
        }

        &__handle {
            &-line {
                width: 8px;
                height: 1px;
                background-color: $blue-4;
                margin-bottom: 1px;
                box-shadow: 0 1px $blue-3, 1px 1px $blue-3, -1px 0 $grey-2;
            }
        }
    }
</style>