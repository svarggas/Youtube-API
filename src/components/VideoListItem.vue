<template>
  <li class="list-group-item media" @click="onVideoSelect">
    <div class="mr-3" width="18%">
      <img :src="getImg" width="100%" />
    </div>

    <div class="media-body">
      <span class="title">{{ video.snippet.title }}</span>
      <br />
      <p>{{ video.snippet.description }}</p>
    </div>
  </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: ["video"],
  computed: {
    getImg() {
      return this.video.snippet.thumbnails.default.url;
    },
  },
  methods: {
    onVideoSelect() {
      this.$emit("videoSelect", this.video);
    },
  },
};
</script>

<style scoped>
li {
  display: flex;
  cursor: pointer;
  background: #131313;
  border: 1px solid #323232;
  color: white;
}
li:hover {
  border: 1px solid lightgray;
}
p {
  font-size: 12px;
}
.title {
  font-size: 16px;
  font-weight: bold;
}
</style>