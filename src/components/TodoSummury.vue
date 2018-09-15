<template>
    <div id="summary_container">
        <a href="#">Total <span class="badge">{{getTotalCount}}</span></a>
        <a href="#">Finished <span class="badge">{{getFinishedCount}}</span></a>
        <a href="#">NotFinished <span class="badge">{{getNotFinishedCount}}</span></a>
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
