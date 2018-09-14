<template>

    <div class="row">
        <div class="glyphicon glyphicon-ok" aria-hidden="true" v-show="isFinished"></div>
        <div>
            <div v-show="!isEditMode" @click="setEditMode">
                {{todoItem.todo}}
            </div>
            
            <div class="input-group" v-show="isEditMode">
                <input type="text"  class="form-control" v-model="editValue">
                <span class="input-group-btn">
                    <button @click="toggleFinish" class="btn btn-default">toggleFinish</button>
                    <button @click="onClickOk" class="btn btn-default">ok</button>
                    <button @click="onClickCancle"
                            class="btn btn-default">cancle</button>
                    <button @click="onClickDelete"
                            class="btn btn-danger">delete</button>                        
                </span>
            </div>
        </div> 
    </div>
</template>

<script>
    export default {
        props : {
            todoItem : {
                type : Object,
            },
            index : {
                type : Number
            }
        },
        data () {
            return {
                isEditMode : false,
                isFinished : this.todoItem.isFinished,
                editValue : this.todoItem.todo                         
            }
        },
        methods : {
            setEditMode : function(){
                this.isEditMode = true;
            },
            setViewMode : function(){
                this.isEditMode = false;
            },
            toggleFinish : function(){
                this.isFinished = !this.isFinished;

                var tempTodoItem = this.todoItem;
                tempTodoItem.isFinished = this.isFinished;

                this.$emit('onChangeValue', this.index, this.todoItem, tempTodoItem)
            },
            onClickOk : function(){
                if(this.editValue.length != 0){
                    if(this.editValue != this.todoItem.todo){
                        this.$emit('onChangeValue', this.index, this.todoItem, {
                            todo : this.editValue,
                            createdDate : new Date()
                        });
                    }
                }

                this.setViewMode();                
            },
            onClickCancle : function(){                          
                this.setViewMode();
                this.editValue = this.todoItem.todo;
            },
            onClickDelete : function(){
                this.$emit('onDeleteItem', this.index)                
            }
        }
    }
</script>

<style>

</style>
