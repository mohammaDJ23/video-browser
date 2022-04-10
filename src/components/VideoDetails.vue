<template>
  <div v-if="video.snippet" class="col-md-8">
    <div class="embed-responsive embed-responsive-16by9">
      <iframe :src="videoUrl" class="embed-responsive-item" frameborder="0" allowfullscreen />
    </div>

    <div class="details">
      <h4>{{ video.snippet.title }}</h4>
      <p>{{ video.snippet.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'VideoDetails',
  props: {
    video: {
      type: Object,
      required: true,
    },
  },
  computed: {
    videoUrl() {
      return `https://youtube.com/embed/${this.video.id.videoId}`;
    },
  },
};
</script>

<style scoped>
.details {
  margin-top: 10px;
  padding: 10px;
  border: 1px solid black;
  border-radius: 4px;
}

iframe {
  width: 100%;
  height: 100%;
}
</style>
