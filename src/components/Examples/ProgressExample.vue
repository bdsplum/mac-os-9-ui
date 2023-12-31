<template>
    <Example name="ProgressBar">
        <template #component>
            <ProgressBar 
                :value="value"
            />
        </template>
        <template #docs>
            A progress bar component.
            <ul>
                <li>
                    value
                    <ul>
                        <li>Number</li>
                        <li>The value of the progress bar (0-100)</li>
                    </ul>
                </li>
            </ul>
        </template>
    </Example>
</template>

<script setup>
    import ProgressBar from '../ProgressBar.vue';
    import Example from './Example.vue';
    import { ref } from 'vue';

    const value = ref(0);
    let direction = 1;
    setInterval(() => {
        value.value += direction;
        if(value.value === 100 || value.value === 0) {
            direction = -1 * direction;
        }
    }, 500);
</script>

<style lang="scss" scoped>
</style>