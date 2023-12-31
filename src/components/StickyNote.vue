<template>
    <div 
        class="sticky"
        :style="{ height: `${height}px`, width: `${width}px` }"
        :class="`sticky--${theme}`"
    >
        <slot />
    </div>
</template>

<script setup>
    const props = defineProps({
        /**
         * Optional sticky height
         */
        height: Number,
        /**
         * Optional sticky width
         */
        width: Number,
        /**
         * The sticky theme - 'yellow', 'grey', 'blue', 'green' or 'red'
         */
        theme: {
            type: String,
            default: 'yellow'
        }
    });
</script>

<style lang="scss" scoped>
    @import "../styles/colours";

    .sticky {
        font-family: Monaco, sans-serif;
        font-size: 12px;
        padding: 5px;
        border: 1px solid;
        overflow: hidden;
        height: fit-content;
        width: fit-content;

        &--yellow {
            background-color: $yellow-1;
            border-color: white $yellow-2 $yellow-2 white;
        }

        &--green {
            background-color: $green-1;
            border-color: white $green-2 $green-2 white;
        }

        &--red {
            background-color: $red-1;
            border-color: white $red-2 $red-2 white;
        }

        &--blue {
            background-color: $blue-4;
            border-color: white $blue-1 $blue-1 white;
        }

        &--grey {
            background-color: $grey-2;
            border-color: white $grey-7 $grey-7 white;
        }
    }
</style>