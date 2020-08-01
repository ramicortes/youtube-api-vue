<template>
  <ul class="list-group col-md-4">
      <VideoListItem 
        v-for="video in videos" 
        :key="video.etag" 
        :video="video"
        @video-select="onVideoSelect" />
  </ul>
</template>

<script>
import VideoListItem from '@/components/VideoListItem.vue';
export default {
    name: 'VideoList',
    components: {
        VideoListItem
    },
    props: {
        videos: {
            type: Array,
            required: false
        }
    },
    methods: {
      onVideoSelect(video) {
        this.$emit('video-select', video)
      }
    }
}
</script>

<style>
    
</style>