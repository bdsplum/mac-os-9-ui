<template>
    <Example name="Tabs">
        <template #component>
            <Tabs
                v-model="value"
                :items="items"
                class="tabs-example"
            >
                <template #0>Some tab content</template>
                <template #1>Some better tab content</template>
                <template #2>The best tab content</template>
            </Tabs>        
        </template>
        <template #docs>
            A Tabs component.
            <ul>
                <li>
                    items
                    <ul>
                        <li>Array[String]</li>
                        <li>A list of tab headers</li>
                    </ul>
                </li>
                <li>
                    value
                    <ul>
                        <li>Number</li>
                        <li>The index of the active tab</li>
                    </ul>
                </li>
            </ul>
        </template>
    </Example>
</template>

<script setup>
    import Tabs from '../Tabs/Tabs.vue';
    import Example from './Example.vue';
    import { ref } from 'vue';

    const value = ref(2);
    const items = ref(['General', 'Views', 'Labels']);
</script>

<style lang="scss" scoped>
    .tabs-example {
        height: 200px;
    }
</style>