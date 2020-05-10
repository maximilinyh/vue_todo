<template>
    <li class="items__item">
        <span class="items__left">
            <span class="items__number">{{index + 1}}</span>
            <input class="items__checkbox"
                   type="checkbox"
                   v-bind:id = 'item.id'
                   v-on:change="item.completed = !item.completed ">
            <label class="items__label"
                   v-bind:class="{done: item.completed}" :for="item.id">
                    {{item.title}}
            </label>
        </span>

        <span class="items__right">
            <button
                    class="items__remove"
                    v-on:click="$emit('remove-item', item.id)">
                remove
            </button>
        </span>
    </li>
</template>


<script>
    export default {
        props: {
            item: {
                type: Object,
                required: true
            },
            index: {
                type: Number,
                required: true
            }
        }
    }
</script>


<style scoped lang="scss">
    .items {
        &__item {
            padding: 0.556rem;
            box-sizing: border-box;
            border: 1px #ddd solid;
            margin-bottom: 0.556rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        &__number {
            margin-right: 0.556rem;
        }

        &__remove {
            cursor: pointer;
        }
        &__label {
            &.done {
                text-decoration: line-through;
            }
        }
    }

</style>