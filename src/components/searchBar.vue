<template>
    <div>
        <input @input="onInput" class="form-control"/>
    </div>
</template>

<script>
    export default {
        name: 'searchBar',
        methods: {
            onInput: function(event){
                this.$emit('termChange', event.target.value);
            }
        }
    }
</script>

<style scoped>
    input{
        width: 75%;
        display: inline-block !important;
    }
    div{
        text-align: center;
        margin: 20px;
    }
</style>