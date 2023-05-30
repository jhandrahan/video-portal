<template>
    <div>
        <input @input="onChange" type="text">
    </div>
</template>

<script>
export default {
    name: 'SearchInput',
    methods:{
        onChange: function(event){
            const term = event.target.value;
            this.$emit('newTerm', term);
        }
    }
}
</script>

<style>

</style>