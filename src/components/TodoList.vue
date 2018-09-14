<template>
    <div class="row">
        <div class="list-group">
            <div class="list-group-item" v-for = "(item, index) in list" :key = "item.todo">  <!-- TODO key is abailable duplicated -->         
                <TodoItemVue v-bind:todoItem="item"
                             v-bind:index="index"
                             @onChangeValue="itemValueChange"
                             @onDeleteItem="deleteItem"></TodoItemVue>                             
            </div>
            
        </div>
    </div>
</template>

<script>
    import TodoItemVue from './TodoItem.vue';

    export default {
        props : {
            list : {
                type : Array                
            }
        },    
        methods : {
            itemValueChange : function(idx, oldObject, newObject){
                this.$emit('onItemValueChange', idx, oldObject, newObject);                
            },
            deleteItem : function(index){
                this.$emit("onDeleteItem", index);
            }  
        },
        components : {
            'TodoItemVue' : TodoItemVue
        }
    }
</script>

<style>

</style>
