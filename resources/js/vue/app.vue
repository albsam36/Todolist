<template>
    <div class="todolist"> 
        <div class="heading">
            <h2  class="title" id="head">To do List</h2>
            <add-item-form
            v-on:reloadlist="getlist()"
            />
        </div>
        <list-view :items="items"
        v-on:reloadlist="getlist()"
        />
    </div>
</template>


<script>
import AddItemForm from './AddItemForm.vue'
import ListView from './ListView.vue'
export default {
    components: {
        AddItemForm,
        ListView,
    },
    setup() {
        
    },
    data:function(){
        return {
            items:[]
        }
    },
    methods: {
        getlist(){
            axios.get('/api/list')
            .then(response =>{
                this.items = response.data
            })
            .catch(error =>{
                console.log(error)
            })
        }
    },
    created(){
        this.getlist();
    }
}
</script>

<style scoped>
.todolist {
    width: 50%;
    margin: auto;
    
}
.heading {
    background-color: rgb(240, 204, 204);
    padding : 10px;
}
.title{
    justify-content: center;
    display: flex;
}
</style>