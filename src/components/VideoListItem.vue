<template>
  <li class="list-group-item media" @click="onVideoSelect">
    <img class="mr-3" :src="img" />
    <div class="media-body">
      {{ video.snippet.title }}
    </div>
  </li>
</template>

<script>
export default {
  name: 'VideoListItem',
  props: {
    video: {
      type: Object,
      required: true,
    },
  },
  computed: {
    img() {
      return this.video.snippet.thumbnails.default.url;
    },
  },
  methods: {
    onVideoSelect() {
      return this.$emit('onVideoSelect', this.video);
    },
  },
};
</script>

<style scoped>
li {
  display: flex;
  cursor: pointer;
}

li:hover {
  background-color: #eee;
}
</style>
