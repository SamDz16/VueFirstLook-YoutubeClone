<template>
  <div class="container">
    <SearchBar @termChange="onTermChange" />
    <div class="row">
      <VideoDetail class="col col-md-8" :video="selectedVideo" />
      <VideoList class="col col-md" :videos="videos" @videoSelect="onVideoSelect" />
    </div>
  </div>
</template>

<script>
import axios from "axios";

import SearchBar from "./components/SearchBar";
import VideoDetail from "./components/VideoDetail";
import VideoList from "./components/VideoList";

const API_KEY = "AIzaSyBX8Ie9JppbsjFg36-RJRg0LJmnNV3BBVI";

export default {
  name: "App",
  components: {
    SearchBar,
    VideoList,
    VideoDetail,
  },
  data: function () {
    return {
      videos: [],
      selectedVideo: null,
    };
  },
  methods: {
    onTermChange: function (searchTerm) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: searchTerm,
          },
        })
        .then(({ data }) => (this.videos = data.items));
    },
    onVideoSelect: function (video) {
      this.selectedVideo = video;
    },
  },
};
</script>
/search
