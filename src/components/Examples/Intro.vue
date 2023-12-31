<template>
    <div class="intro">
        <div class="intro__inner">
            <img 
                class="intro__image"
                :src="finder" 
            />
            <div class="intro__title">Mac OS 9 UI</div>
        </div>
        <p class="intro__text">A collection of Vue 3 components recreating the beautiful styling from Mac OS 9.</p>
    </div>
</template>

<script setup>
    import finder from '../../assets/finder.png';
</script>

<style lang="scss" scoped>
    @import "../../styles/colours";

    .intro {
        margin: auto;
        background-color: $grey-1;
        width: 380px;
        box-shadow: inset 1px 1px white, inset -1px -1px $grey-4;
        border: 1px solid black;
        padding: 30px 60px;
        display: flex;
        flex-direction: column;
        font-size: 14px;

        &__inner {
            background-color: white;
            flex: 1 1 auto;
            border: 1px solid black;
            box-shadow: 1px 1px white, -1px -1px $grey-4;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        &__title {
            font-family: AppleGaramond, sans-serif;
            font-size: 64px;
        }

        &__image {
            width: 130px;
            margin-top: 20px;
        }

        &__text {
            margin-bottom: 0;
            text-align: center;
        }
    }
</style>