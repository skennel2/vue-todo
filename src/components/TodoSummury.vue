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
            list : {
                type : Array                
            }
        },
        computed : {
            getTotalCount : function(){
                return this.list.length;
            },
            getFinishedCount : function (){
                return this.list.filter((i)=>{
                    return i.isFinished;
                }).length;
            },
            getNotFinishedCount : function (){
                return this.list.filter((i)=>{
                    return !i.isFinished;
                }).length;
            }
        }
            
    }
</script>

<style>

</style>
