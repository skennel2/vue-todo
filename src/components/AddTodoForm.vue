<template>
    <div>
        <input type="text" v-model="newTodo"/>
        <button @click="addTodo">add</button>
        <button @click="clearInput">clear</button>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                newTodo : ''
            }
        },
        methods : {
            addTodo : function(){
                this.$emit('addTodo', this.newTodo)
                this.clearInput();
            },
            clearInput : function(){
                this.newTodo = ''
            }
        }
    }
</script>

<style scoped>

</style>
