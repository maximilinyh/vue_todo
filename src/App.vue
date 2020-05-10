<template>
  <div id="app">
    <div class="page-frame">
      <h1>Очередная тудушечка</h1>
      <AddItems
      v-on:add-item = 'handlerAddItem'/>

      <List
        v-bind:items ='items'
        v-on:remove-item = 'handlerRemoveItem'
      />

      <ToolBar
        v-on:filter-completed = 'handlerFilterCompleted'
        v-on:filter-need-too-do="handlerFilterTodoItem"
        v-on:filter-all="handlerShowAllItems"
        v-on:remove-all-items="handlerRemoveAllItems"
      />
      <!--    <router-view/>-->
    </div>
  </div>
</template>


<script>
  import List from "@/components/List";
  import AddItems from '@/components/AddItems'
  import ToolBar from '@/components/ToolBar'

  export default {
    name: 'app',

    mounted(){
      const url = 'https://jsonplaceholder.typicode.com/posts?_limit=3';
        fetch(url).then((response)=>{
          return response.json()
        }).then((result)=> {
          result.map((item)=> {
            item['completed']= false
          })
          this.items = result
        }).catch((error)=> {
          console.log(error.message)
        })
    },
    data() {
      return {
        items: []
      }
    },
    components: {
      List,
      AddItems,
      ToolBar
    },
    methods: {
      handlerRemoveItem(id){
        this.items = this.items.filter((item)=> {
            return item.id !== id;
          })
      },
      handlerAddItem(newItem){
          this.items.push(newItem)
      },

      handlerFilterCompleted() {
        const filterItems = this.items.filter((item)=> {
          return item.completed == true
        })
        this.items = filterItems

      },

      handlerFilterTodoItem(){
        const filterItems = this.items.filter((item)=> {
          return item.completed == false
        })
        this.items = filterItems
      },

      handlerShowAllItems() {
        return this.items
      },

      handlerRemoveAllItems() {
        this.items = []
      }
    }
  }
</script>


<style  lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Source+Sans+Pro&display=swap');
  body {
    font-family: 'Source Sans Pro', sans-serif;
  }
.page-frame {
  max-width: 1200px;
  padding: 0 1.111rem;
  margin: 0 auto;
}

</style>

