<template>
    <Example name="StickyNote">
        <template #component>
            <StickyNote 
                width="200" 
                height="150"
            >
                A yellow sticky!
            </StickyNote>
            <StickyNote 
                width="200" 
                height="150"
                theme="blue"
            >
                A blue sticky!
            </StickyNote>
            <StickyNote 
                width="200" 
                height="150"
                theme="grey"
            >
                A grey sticky!
            </StickyNote>
        </template>
        <template #docs>
            A generic card component in the style of a sticky note.
            <ul>
                <li>width</li>
                <li>height</li>
                <li>theme</li>
            </ul>
        </template>
    </Example>
</template>

<script setup>
    import StickyNote from '../StickyNote.vue';
    import Example from './Example.vue';
</script>

<style lang="scss" scoped>
    
</style>