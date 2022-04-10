<template>
  <ul class="list-group">
    <VideoListItem v-for="video in videos" :key="video.id.videoId" :video="video" @onVideoSelect="onVideoSelect" />
  </ul>
</template>

<script>
import VideoListItem from './VideoListItem.vue';

export default {
  name: 'VideoList',
  components: {
    VideoListItem,
  },
  props: {
    videos: {
      type: Array,
      required: true,
    },
  },
  methods: {
    onVideoSelect(video) {
      return this.$emit('onVideoSelect', video);
    },
  },
};
</script>
