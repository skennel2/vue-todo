<template>
    <ul>
        <li v-for = "(item, index) in list">
            {{item.todo}}
        </li>
    </ul>
</template>

<script>
    export default {
        props : {
            list : {
                type : Array                
            }
        },
    }
</script>

<style>

</style>
