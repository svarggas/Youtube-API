<template>
  <div v-if="video" class="col-md-12 video">
    <div class="embed-responsive embed-responsive-16by9">
      <iframe :src="videoUrl" class="embed-responsive-item"></iframe>
    </div>
    <div class="details">
      <h4>{{ video.snippet.title }}</h4>
      <p>{{ video.snippet.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "VideoDetail",
  props: ["video"],
  computed: {
    videoUrl() {
      return `https://www.youtube.com/embed/${this.video.id.videoId}`;
    },
  },
};
</script>

<style scoped>
.details {
  margin-top: 10px;
  margin-bottom: 10px;
  padding: 10px;
  border: 1px solid #323232;
  border-radius: 4px;
  color: lightgray;
}
.details h4 {
  color: white;
}
.video {
  padding-left: 0px;
  width: 100%;
}
.embed-responsive {
  border-radius: 10px;
}
</style>