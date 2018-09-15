<template>
    <div>
        <div>요약</div>
        <div>{{getFinishedCount}}</div>
        <div>{{getNotFinishedCount}}</div>
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
            getFinishedCount : function (){
                return list.filter((i)=>{
                    return i.isFinished;
                }).length;
            },
            getNotFinishedCount : function (){
                return list.filter((i)=>{
                    return !i.isFinished;
                }).length;
            }
        }
            
    }
</script>

<style>

</style>
