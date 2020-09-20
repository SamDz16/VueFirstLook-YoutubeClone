<template>
  <ul class="list-group">
    <VideoListItem
      v-for="video in videos"
      :video="video"
      :key="video.id.videoId"
      @videoSelect="onVideoSelect"
    ></VideoListItem>
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem";

export default {
  name: "VideoList",
  components: {
    VideoListItem,
  },
  props: {
    videos: Array,
  },
  methods: {
    onVideoSelect: function (video) {
      this.$emit("videoSelect", video);
    },
  },
};
</script>

<style></style>
