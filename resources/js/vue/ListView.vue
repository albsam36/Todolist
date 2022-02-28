<template>
    <div>
        <div v-for="(item,index) in items" :key="index">
            <list-item-view
                :item="item"
                v-on:itemchanged="$emit('reloadlist')" />
        </div>     

    </div>
</template>

<script>
import ListItemView from './ListItemView.vue'

export default {
  components: { ListItemView },
    props: ['items'],
    setup() {
        
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
}
</script>