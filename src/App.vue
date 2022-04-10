<template>
  <div class="container">
    <!-- v-on:termChange -->
    <SearchBar @termChange="onTermChange" />

    <div class="row">
      <VideoDetails :video="selectedVideo" />

      <!-- v-bind:termChange -->
      <VideoList :videos="videos" @onVideoSelect="onVideoSelect" />
    </div>
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue';
import VideoList from './components/VideoList.vue';
import VideoDetails from './components/VideoDetails.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
    VideoDetails,
  },
  data() {
    return {
      videos: [],
      selectedVideo: {},
    };
  },
  methods: {
    onTermChange(value) {
      axios
        .get('https://www.googleapis.com/youtube/v3/search', {
          params: {
            key: 'AIzaSyDKn13pmPU4jUNnrYFHDv5ekv187dhRkzc',
            type: 'video',
            part: 'snippet',
            q: value,
          },
        })
        .then(res => {
          this.videos = res.data.items;
        });
    },
    onVideoSelect(video) {
      this.selectedVideo = video;
    },
  },
};
</script>

<style>
#app {
}
</style>
