<template>
    <div class="headerlist">
        <input class="checkbox" type="checkbox"
        @change="updateCheck()"
        v-model="item.completed" />
        <span class ="list"> {{item.list}} </span>
        <button  class="buttonlist" type="button"
        @click="DeleteItem()"
        > Delete </button>

    </div>
</template>

<script>
export default {
    props: ['item'],
    setup() {
        
    },
    methods:{
        DeleteItem(){
            axios.delete('api/list/' + this.item.id)
            .then(response => {
                if(response.statusCode == 200){
                   this.$emit('itemchanged');
                }
            })
            .catch(error => {
                console.log(error);
            })
        }
    }
}
</script>
<style scoped>
.list {
    width: 100%;
    margin-left: 20px;
}
.headerlist{
    display: flex;
}
.buttonlist{
    margin: left 30px;
}
</style>