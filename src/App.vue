<script setup>
    import ScrollContainer from './components/Scroll/ScrollContainer.vue';
    import Card from './components/Card.vue';
</script>

<template>
    <ScrollContainer>
        <div class="content">
            <Card 
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
                    Some text!
                </template>
            </Card>
        </div>
    </ScrollContainer>
</template>

<style scoped lang="scss">
    .content {
        padding: 20px;
    }
</style>
