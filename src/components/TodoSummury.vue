<template>
    <div id="summary_container">
        <div href="#">Total <span class="badge">{{getTotalCount}}</span></div>
        <div href="#">Finished <span class="badge">{{getFinishedCount}}</span></div>
        <div href="#">NotFinished <span class="badge">{{getNotFinishedCount}}</span></div>
    </div>
</template>

<script>
    export default {
        props : {
            todoList : {
                type : Array                
            }
        },
        computed : {
            getTotalCount : function(){
                return this.todoList.length;
            },
            getFinishedCount : function (){
                return this.todoList.filter((i)=>{
                    return i.isFinished;
                }).length;
            },
            getNotFinishedCount : function (){
                return this.todoList.filter((i)=>{
                    return !i.isFinished;
                }).length;
            }
        }
            
    }
</script>

<style>

</style>
