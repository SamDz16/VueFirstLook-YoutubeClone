<template>
  <li @click="onVideoSelect" class="list-group-item">
    <img class="mr-3" :src="thumbnailUrl" alt="pic" />
    <div class="media-body">{{ video.snippet.title }}</div>
  </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: ["video"],
  computed: {
    thumbnailUrl: function () {
      return this.video.snippet.thumbnails.default.url;
    },
  },
  methods: {
    onVideoSelect: function () {
      this.$emit("videoSelect", this.video);
    },
  },
};
</script>

<style scoped>
li {
  display: flex;
  cursor: pointer;
  align-items: start;
}

li:hover {
  background-color: #eee;
}
</style>
