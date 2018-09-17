<template>
    <div class="row">
        <div>
            <span class="glyphicon glyphicon-ok" 
                  v-bind:class = "{'finished' : isFinished, 'notFinished' : !isFinished}"
                  aria-hidden="true" 
                  @click="toggleFinish"></span>    
            <span v-show="!isEditMode" @click="setEditMode">
                {{todoItem.todo}}
            </span>
            
            <span class="input-group" v-show="isEditMode">
                <input type="text"  class="form-control" v-model="editValue">
                <span class="input-group-btn">
                    <button @click="saveChanges" class="btn btn-default">ok</button>
                    <button @click="cancleChanges"
                            class="btn btn-default">cancle</button>                       
                </span>
            </span>
            <span class="glyphicon glyphicon-remove danger" @click="deleteItem"></span> 
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

                let tempTodoItem = this.todoItem;
                tempTodoItem.todo = this.editValue,
                tempTodoItem.isFinished = this.isFinished;
                tempTodoItem.modifiedDate = new Date();

                this.$emit('onChangeValue', this.index, this.todoItem, tempTodoItem);

                this.setViewMode(); 
            },
            saveChanges : function(){
                if(this.editValue.length != 0){
                    if(this.editValue != this.todoItem.todo){
                        this.$emit('onChangeValue', this.index, this.todoItem, {
                            todo : this.editValue,                            
                            isFinished : this.isFinished,
                            modifiedDate : new Date(),
                        });
                    }
                }

                this.setViewMode();                
            },
            cancleChanges : function(){                          
                this.setViewMode();
                this.editValue = this.todoItem.todo;
            },
            deleteItem : function(){
                this.$emit('onDeleteItem', this.index)                
            }
        }
    }
</script>

<style>
    .finished {
        color : cornflowerblue
    }
    .notFinished {
        color : gray
    }
    .danger {
        color : crimson
    }
</style>
