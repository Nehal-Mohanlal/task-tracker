<template>
    <button @click="onClick()" :style="{background:color}" class="btn">{{text}}</button>

</template>

<script> 
    export default{
        name: 'buttonOne', 
        props:{
            text:String, 
            color:String
        },
        methods:{
            onClick(){
                console.log("button has been clicked")
            }
        }
    }
</script>