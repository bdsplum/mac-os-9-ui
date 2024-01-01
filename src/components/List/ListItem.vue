<template>
    <a 
        class="list-item"
        :class="{ 'list-item--disabled': disabled }"
        :href="href"
        @click="emits('click')"
    >
        <slot />
    </a>
</template>

<script setup>
    const props = defineProps({
        /**
         * Whether the item is disabled
         */
        disabled: Boolean,
        /**
         * An optional target
         */
        href: String
    });

    const emits = defineEmits(['click']);
</script>

<style lang="scss" scoped>
    @import "../../styles/colours";

    .list-item {
        font-size: 14px;
        padding: 1px 15px;
        cursor: pointer;
        text-decoration: none;
        color: black;

        &--disabled {
            cursor: default;
            color: $grey-5;
        }

        &:hover:not(.list-item--disabled) {
            color: white;
            background-color: $blue-3;
        }
    }
</style>