<template>
    <ul>
        <!--v-for directive is where we want to build a list  -->
        <!-- v-bind:key="video.id"--this assigns a unique id to each item that renders to tell them apart -->
        <Item v-for="video in videos" v-bind:key="video.id" v-bind:video="video"></Item>
    </ul>
</template>

<script>
import Item from "./Item.vue";
export default {
    name: "Videos",
    props:{
        videos: [],
    },
    components:{
        Item,
    },
};
</script>

<style>
ul{
    list-style: none;
    margin: 0;
    padding: 0;
}
</style>