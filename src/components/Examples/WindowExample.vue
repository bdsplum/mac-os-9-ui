<template>
    <Example name="Window">
        <template #component>
            <Window 
                width="700" 
                height="400"
            >
                <template #header>
                    Header text
                </template>
                <template #subheader>
                    Subheader text
                </template>
                <template #default>
                    <p>Here is some really interesting information to show in a card:</p>
                    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce porttitor felis in urna vestibulum, vel suscipit lorem placerat. Ut sed eros sodales, lacinia lectus et, suscipit magna. Pellentesque tortor eros, tempor sagittis interdum id, tincidunt quis metus. Integer lorem tellus, ultricies vitae condimentum vitae, gravida nec mi. Nullam at neque sem. Nulla congue luctus nunc ac dictum. In porta velit cursus tempor porta. Curabitur dapibus pulvinar sapien eu fringilla. Quisque pharetra ligula sit amet magna efficitur pharetra. Morbi commodo gravida rhoncus. Cras quis elit arcu. Pellentesque elit felis, fermentum et efficitur nec, elementum ornare sem. Integer nec lacus ac magna condimentum euismod.</p>
                </template>
            </Window>
        </template>
        <template #docs>
            A generic card component in the style of a finder window.
            <ul>
                <li>
                    width
                    <ul>
                        <li>Number</li>
                        <li>Optional width in pixels of the window</li>
                    </ul>
                </li>
                <li>
                    height
                    <ul>
                        <li>Number</li>
                        <li>Optional height in pixels of the window</li>
                    </ul>
                </li>            
            </ul>
        </template>
    </Example>
</template>

<script setup>
    import Window from '../Window.vue';
    import Example from './Example.vue';
</script>

<style lang="scss" scoped>
    
</style>