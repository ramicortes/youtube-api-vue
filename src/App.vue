<template>
  <div class="container">
    <SearchBar @term-change="onTermChange" />
    <div class="row">
      <VideoDetail 
        :video="selectedVideo"/>
      <VideoList 
        :videos="videos"
        @video-select="onVideoSelect" />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from '@/components/SearchBar.vue';
import VideoList from '@/components/VideoList.vue';
import VideoDetail from '@/components/VideoDetail.vue';
const API_KEY = 'AIzaSyCLac6apE6RmQSVPkKf3PYv-ROYeO5ywEU';

export default {
    name: 'App',
    data() {
      return {
        videos: [],
        selectedVideo: null
      }
    },
    components: {
      SearchBar,
      VideoList,
      VideoDetail
    },
    methods: {
      onTermChange(searchTerm) {
        axios.get('https://www.googleapis.com/youtube/v3/search', {
          params: {
            key: API_KEY,
            type: 'video',
            part: 'snippet',
            q: searchTerm
          }
        }).then(response => this.videos = response.data.items)
      },
      onVideoSelect(video) {
        this.selectedVideo = video;
      }
    }
}
</script>

<style>

</style>