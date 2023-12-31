<template>
    <Example name="List">
        <template #component>
            <List class="list-example">
                <ListItem>Option 1</ListItem>
                <ListItem>Option 2</ListItem>
                <ListItem disabled>Option 3</ListItem>
                <ListDivider />
                <ListItem>Option 4</ListItem>
                <ListItem>Option 5</ListItem>
            </List>
        </template>
        <template #docs>
            A List component.
            <ul>
                <li>
                    disabled
                    <ul>
                        <li>Boolean</li>
                        <li>Disables the item</li>
                    </ul>
                </li>
            </ul>
        </template>
    </Example>
</template>

<script setup>
    import List from '../List/List.vue';
    import ListItem from '../List/ListItem.vue';
    import ListDivider from '../List/ListDivider.vue';
    import Example from './Example.vue';
</script>

<style lang="scss" scoped>
    .list-example {
        margin: auto;
    }
</style>