<template>
    <div class="items-toolbar">
        <button class="items-toolbar__btn" v-on:click="$emit('filter-all')">Show all</button>
        <button class="items-toolbar__btn" v-on:click="$emit('filter-completed')">Show completed</button>
        <button class="items-toolbar__btn" v-on:click="$emit('filter-need-too-do')">Need to do</button>
        <button class="items-toolbar__btn" v-on:click="$emit('remove-all-items')">Remove all</button>
    </div>
</template>


<style scoped lang="scss">
    .items-toolbar {
        margin-top: 1.111rem;
        &__btn {
            margin-right: 1.111rem;
            cursor: pointer;
        }
    }
</style>