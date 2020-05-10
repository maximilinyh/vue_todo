<template>
    <div class="add-items">
        <form class="add-items__form" v-on:submit.prevent="handlerSubmit">
            <input class="add-items__input" type="text" v-model="title">
            <button class="add-items__submit" type='submit'>Add item</button>
        </form>
    </div>
</template>


<script>
    export default  {
        data() {
            return {
                title: ''
            }
        },

        methods: {
            handlerSubmit() {
                if(this.title.trim()){
                    const newItem = {
                        title: this.title,
                        completed: false,
                        id: Date.now()
                    }
                    this.$emit('add-item', newItem )
                    this.title = ''
                }
            }
        }
    }
</script>

<style scoped lang="scss">
    .add-items {
        margin-bottom: 1.111rem;
    }
</style>