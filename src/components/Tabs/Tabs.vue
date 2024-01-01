<template>
    <div class="tabs">
        <div class="tabs__buttons">
            <TabButton
                v-for="(tab, i) in items"
                :key="tab"
                :active="modelValue === i"
                @click="emits('update:modelValue', i)"
            >
                {{ tab }}
            </TabButton>
        </div>
        <div class="tabs__content">
            <slot :name="modelValue" />
        </div>
    </div>
</template>

<script setup>
    import TabButton from './TabButton.vue';

    const props = defineProps({
        /**
         * The list of tabs
         */
        items: Array,
        /**
         * The index of the active tab
         */
        modelValue: {
            type: Number,
            default: 0
        }
    });

    const emits = defineEmits(['update:modelValue']);
</script>

<style lang="scss" scoped>
    @import "../../styles/colours";

    .tabs {
        display: flex;
        flex-direction: column;

        &__content {
            width: 100%;
            border: 1px solid black;
            flex: 1;
            background-color: $grey-2;
            box-shadow: inset 1px 1px white, inset -1px -1px $grey-3;
            margin-top: -1px;
            font-size: 12px;
            padding: 8px;
            box-sizing: border-box;
        }

        &__buttons {
            display: flex;
        }
    }
</style>