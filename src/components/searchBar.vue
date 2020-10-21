<template>
    <div>
        <input @input="onInput" class="form-control" placeholder="Search"/>
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
    input, input:focus{
        width: 75%;
        display: inline-block !important;
        background: #131313;
        border: 1px solid #323232;
        margin-top: 20px;
    }
    div{
        text-align: center;
        margin: 20px;
    }
</style>