<template>
    <ul class="list-group col-md-4">
        <video-list-item v-for='video in videos' 
        :key="video.etag"
        :video= 'video'
        @videoSelect= "onVideoSelect"/>
    </ul>
</template>

<script>
import VideoListItem from './VideoListItem.vue'
export default {
  components: { VideoListItem },
    name: 'VideoList',
    props: ["videos"],
    methods: {
        onVideoSelect(video){
            this.$emit("videoSelect", video)
        }
    }
}
</script>