<template>

    <div  class="row">
        <div v-show="!isEditMode" @click="setEditMode">
            {{todoItem.todo}}
        </div>

        <div class="input-group" v-show="isEditMode">
            <input type="text"  class="form-control" v-model="editValue">
            <span class="input-group-btn">
                <button @click="onClickOk" class="btn btn-primary">ok</button>
                <button @click="onClickCancle" class="btn btn-primary">cancle</button>
            </span>
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
            }
        }
    }
</script>

<style>

</style>
