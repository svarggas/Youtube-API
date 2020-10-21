<template>
    <li class="list-group-item media" @click="onVideoSelect">
        <img class="mr-3" :src="getImg" /> 
        <div class="media-body">
            {{ video.snippet.title }}<br>
            {{ video.snippet.description }}
        </div>
    </li>
</template>

<script>
    export default {
        name: 'VideoListItem',
        props: ['video'],
        computed: {
            getImg() {
                return this.video.snippet.thumbnails.default.url
            }
        },
        methods: {
            onVideoSelect() {
                this.$emit('videoSelect', this.video)
            }
        } 
    }
</script>

<style scoped>
    li{
        display: flex;
        cursor: pointer;
        background: #131313;
        border: 1px solid #323232;
        color: white;
    }
    li:hover{
        border: 1px solid lightgray;
    }
</style>