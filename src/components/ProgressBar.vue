<template>
    <div class="progress">
        <div 
            class="progress__bar"
            :style="{ width }"
        />
    </div>
</template>

<script setup>
    import { computed } from 'vue';

    const props = defineProps({
        /**
         * The percentage value (0-100)
         */
        value: Number
    });

    const width = computed(() => {
        let w = props.value;
        if(!w || w < 0) {
            w = 0;
        } else if(w > 100) {
            w = 100;
        }

        return `${w}%`;
    });
</script>

<style lang="scss" scoped>
    @import "../styles/colours";

    .progress {
        width: 100%;
        height: 16px;
        background-color: $grey-7;
        box-shadow: inset 1px 1px $grey-6, inset -1px -1px $grey-1, -1px -1px $grey-4, 1px 1px white;
        border: 1px solid  black;
        display: flex;
        overflow: hidden;

        &__bar {
            border-right: 1px solid black;
            justify-content: flex-start;
            background: linear-gradient(180deg, rgba(51,51,153,1) 0%, rgba(102,102,203,1) 12%, rgba(153,153,255,1) 25%, rgba(204,203,255,1) 38%, rgba(255,255,255,1) 51%, rgba(204,203,255,1) 61%, rgba(153,153,255,1) 73%, rgba(102,102,203,1) 86%, rgba(51,51,153,1) 93%, rgba(2,0,85,1) 100%);            
            box-shadow: 1px 0 $grey-9, 2px 0 $grey-6;
            transition: width 0.2s;
        }
    }
</style>