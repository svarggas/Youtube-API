<template>
    <div class="container">
        <SearchBar @termChange="onTermChange"></SearchBar>
        <div class="row" >
            <div v-show="selectedVideo !== null">
                <VideoDetail :video="selectedVideo"></VideoDetail>
                <VideoList :videos="videos" @videoSelect="onVideoSelect"></VideoList>
            </div>
            <div v-show="selectedVideo == null" class="row noSearch">
                <img src="../public/youtubeLike.png">
                <h1>Search for a topic to<br> show related videos</h1>
            </div>
        </div>        
    </div>
</template>

<script>
    import axios from 'axios'
    import SearchBar from './components/searchBar';
    import VideoList from './components/VideoList';
    import VideoDetail from './components/videoDetail'
    const API_KEY = 'AIzaSyD2fMI3yBzxEpchkJk11SAM8P1fj79DkeY';

    export default {
        name: 'App',
        components: {
            SearchBar,
            VideoList,
            VideoDetail
        },
        data() {
            return {
                videos: [],
                selectedVideo: null
            }
        },
        methods: {
            onTermChange(searchTerm){
                axios.get('https://www.googleapis.com/youtube/v3/search',{
                    params: {
                        key: API_KEY,
                        type: 'videos',
                        part: 'snippet',
                        q: searchTerm,
                        maxResults: 5
                    }
                }).then(response => {
                    this.videos = response.data.items
                })
            },
            onVideoSelect(video){
                this.selectedVideo = video
            }
        }
    }
</script>
 
<style>
    .container{
        background-color: #212121;
        height: 95vh;
        border-radius: 15px;
    }
    .noSearch{
        color: lightgray;
        text-align: center;
        display: block;
        padding-bottom: 35px;
        width: 100%;
    }
    .row{
        margin: 0 20px 0 20px;
        align-items: center;
    }
    img{
        max-width: 512px;
        max-height: 512px;
        height: auto;
        width: 100%;
    }
</style>