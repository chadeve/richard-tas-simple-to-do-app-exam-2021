<template>
    <div>
        <div v-for="(item,index) in items" :key = "index">
            <list-task
                :item="item"
                class="task"
                v-on:itemchanged="$emit('reloadlist')"
                />
        </div>
    </div>
</template>
<script>

import listTask from "./listTask"
// import ListTask from '.listTask.vue'
export default {
    props:['items'],
    components:{
        listTask
    }
    
}
</script>
<style scoped>
.task{
    background: #e6e6e6;
    padding: 5px;
    margin-top: 5px;
}
</style>