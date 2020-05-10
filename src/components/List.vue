<template>
<div class="items">
    <ul class="items__list">
       <ListItem
               v-for="(item, index) in items"
               v-bind:item='item' :key="item.id" :index ='index'
               v-on:remove-item="handlerRemoveItem"
       />
    </ul>
</div>
</template>

<script>
    import ListItem from '@/components/ListItem'
    export default {
        props: {
            items: {
                type: Array,
                required: true
            }
        },
        components: {
            ListItem
        },
        methods: {
            handlerRemoveItem(id){
                this.$emit('remove-item',id)
            }
        }
    }
</script>

<style scoped lang="scss">
.items {
    &__list {
        padding: 0;
        margin: 0;
        list-style: none;
     }
}
</style>