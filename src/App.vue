<template>
  <div class="container">
    <!-- v-on:termChange -->
    <SearchBar @termChange="onTermChange" />

    <!-- v-bind:termChange -->
    <VideoList :videos="videos" @onVideoSelect="onVideoSelect" />
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue';
import VideoList from './components/VideoList.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
  },
  data() {
    return {
      videos: [],
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
      console.log(video);
    },
  },
};
</script>

<style>
#app {
}
</style>
