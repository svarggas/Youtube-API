<template>
    <div class="container">
        <SearchBar @termChange="onTermChange"></SearchBar>
        <div class="row">
            <VideoDetail :video="selectedVideo"></VideoDetail>
            <VideoList :videos="videos" @videoSelect="onVideoSelect"></VideoList>
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
                        q: searchTerm
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