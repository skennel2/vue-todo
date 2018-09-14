<template>
    <ul>
        <li v-for = "(todo, index) in list">
            {{todo}}
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
