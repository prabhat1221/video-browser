<template>
    <div v-if="video" class="col-md-8">
        <div class="ratio ratio-16x9">
            <iframe :src="videoUrl" frameborder="0"></iframe>
        </div>
        <div class="details">
            <h4>{{video.snippet.title}}</h4>
            <p>{{video.snippet.description}} </p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'VideoDetails',
    props: ['video'],
    computed: {
        videoUrl() {
            const {videoId} = this.video.id
            return `https://www.youtube.com/embed/${videoId}`
        }
    }
}
</script>

<style scoped>
.details{
    margin: 10px;
    padding: auto;
    border: 2px solid #ddd;
}
</style>>