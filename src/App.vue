<template>
  <div id="app">
    <h1>Youtube-App</h1>
    <SearchBar  @changeData="logData"/>
    <div class="row">
      <VideoDetail :video = "selectedVideo"/>
      <VideoList :videos = "videos"
        @videoSelect = "onVideoSelect"
      ></VideoList>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/searchBar.vue';
import VideoList from './components/VideoList.vue';
import VideoDetail from './components/videoDetail.vue';
const API_KEY = 'AIzaSyAma_6O6zM6iRmsUzAghw1ersIMoxwtFyY';
export default {
  name: 'app',
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data: function () {
    return {
      videos: [],
      selectedVideo: null
    };
  },
  methods: {
    onVideoSelect(video) {
      this.selectedVideo = video;
    },
    logData(searchTerm) {
      axios
      .get('https://www.googleapis.com/youtube/v3/search', {
        params: {
          key: API_KEY,
          type: 'video',
          part: 'snippet',
          q: searchTerm
        }
      })
      .then(response => {
        this.videos = response.data.items;
      });
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
