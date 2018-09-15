<template>
    <div id="summary_container">
        <div>요약</div>
        <span>Finished : {{getFinishedCount}}</span>
        <span>NotFinished : {{getNotFinishedCount}}</span>
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
                console.log(this.list)
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
