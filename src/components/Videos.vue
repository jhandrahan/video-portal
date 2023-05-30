<template>
    <ul>
        Videos
        
    </ul>
</template>

<script>
import Item from "./Item.vue";
export default {
    name: "Videos",
    props:["videos"],
    components:{
        Item,
    },
};
</script>

<style>
</style>