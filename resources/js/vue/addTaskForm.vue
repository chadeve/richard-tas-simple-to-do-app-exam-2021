<template>
    <div class="addTask">
        <input type="text" v-model="item.task" />
        <font-awesome-icon 
            icon = "plus-square"
            @click="addTask()"
            :class="[ item.task ? 'active' : 'inactive', 'plus']"
        />
    </div>
</template>
<script>
export default {
    data: function(){
        return{
            item:{
                task:""
            }
        }
    },
    methods: {
        addTask(){
            if( this.item.task == ''){
                return;
            }
            axios.post('api/item/store',{
                item:this.item
            })
            .then(response => {
                if(response.status == 201){
                    console.log(this.item.task);
                    this.item.task == "";
                    this.$emit('reloadlist');
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
.addTask{
    display: flex;
    justify-content: center;
    align-items: center;
}
input{
    background: #f7f7f7;
    border: 0px;
    outline: none;
    padding: 5px;
    margin-right: 10px;
    width: 100%;

}
.plus{
    font-size: 20px;
}
.active{
    color: #00CE25;

}
.inactive{
    color: #999999;
}
</style>