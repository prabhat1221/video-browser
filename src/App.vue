<template>
    <div class="container">
        <search-bar @termChange= 'onTermChange'/>
        <div class="row ">
            <video-details :video="video" />
            <video-list :videos= "videos" @videoSelect="onVideoSelect"/>    
        </div>
    </div>
</template>

<script>
import axios from 'axios'
import SearchBar from './components/SearchBar.vue'
import VideoList from './components/VideoList.vue'
import VideoDetails from './components/VideoDetails.vue'
const API_KEY = 'AIzaSyBP4V1cJMghgCqKiyOJFwrOcUgcseKzlxk'
export default {
  components: { SearchBar, VideoList, VideoDetails},
    name: 'App',
    data(){
        return {videos: [], video: null }
    },
    methods: {
        onVideoSelect(video){
            this.video = video
        },
        onTermChange(searchTerm){
            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params: {
                    key: API_KEY,
                    type: 'video',
                    part:'snippet',
                    q: searchTerm
                }
			}).then(response => {
                this.videos = response.data.items
            })
        },
    }
}
</script>

<style scoped>

</style>