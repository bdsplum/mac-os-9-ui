<template>
    <Example name="ScrollContainer">
        <template #component>
            <ScrollContainer class="scroll-container">
                <div class="scroll-example">
                    <div class="scroll-example__text">
                        Scroll me down to the right!
                    </div>
                    <div class="scroll-example__text--bottom">
                        Found me!
                    </div>
                </div>
            </ScrollContainer>
        </template>
        <template #docs>
            A virtual scroll component emulating the finder scroll bars.
        </template>
    </Example>
</template>

<script setup>
    import ScrollContainer from '../Scroll/ScrollContainer.vue';
    import Example from './Example.vue';
</script>

<style lang="scss" scoped>
    @import "../../styles/colours";

    .scroll-container {
        width: 400px;
        height: 300px;
        margin: auto;
        padding: 10px;
        background-color: $grey-3;
        border: 1px solid black;
        box-shadow: inset 1px 1px white, inset -1px -1px $grey-8;
    }

    .scroll-example {
        &__text {
            margin-bottom: 600px;

            &--bottom {
                margin-left: 600px;
            }
        }
    }
</style>