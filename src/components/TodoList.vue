<template>
    <div class="row">
        <div class="list-group">
            <div v-for = "(item, index) in list" class="list-group-item" @click="clickItem(index)">           
                <TodoItemVue v-bind:todoItem="item"
                             v-bind:index="index"
                             v-on:onChangeValue="onItemValueChange"></TodoItemVue>                             
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
        data () {
            return {
                isEditMode : false,
            }
        },        
        methods : {
            clickItem : function(index){
                this.isEditMode = true;
            },
            onItemValueChange : function(idx, oldObject, newObject){
                console.log(newObject);
            }        
        },
        components : {
            'TodoItemVue' : TodoItemVue
        }
    }
</script>

<style>

</style>
