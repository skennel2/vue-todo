<template>
    <div class="row">
        <div class="input-group" v-show="isShow">
            <input type="text" v-model="newTodo" class="form-control" />

            <span class="input-group-btn">
                <button @click="addTodo" class="btn btn-primary">add</button>
                <button @click="clearInput" class="btn btn-primary">clear</button>
            </span>
        </div>
    </div>    
</template>

<script>
    export default {
        data(){
            return{
                newTodo : '',
                isShow : true
            }
        },
        methods : {
            addTodo : function(){
                if(this.newTodo.length != 0){
                    var newTodoObj = {
                        todo : this.newTodo,
                        createdDate : new Date()
                    };

                    this.$emit('addTodo', newTodoObj)
                    this.clearInput();
                }
            },
            clearInput : function(){
                this.newTodo = ''            
            }
        }
    }
</script>

<style scoped>

</style>
