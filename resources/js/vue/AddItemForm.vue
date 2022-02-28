<template>
    <div class="addlist">
        <input type="text" v-model="item.list"/> 
        <button 
         @click="addItem()">
         tambah

        </button>
    
    </div>
</template>

<script>
export default {
    data: function(){
        return{
            item:{
                list:""
            }
        }
    },
    methods:{
        addItem(){
            if(this.item.list== ''){
                return;
            }
            axios.post('api/list/store',{
                item: this.item
            })
            .then(response =>{
                if(response.status==201){
                    this.item.list = "";
                    this.$emit('reloadlist');
                }
            })
            .catch(error =>{
                console.log(error);
            })
        }
    },
    setup() {
        
    },
}
</script>
<style scoped>
.addlist{
    display:flex;
    align-items: center;
    justify-content: center;
}
</style>