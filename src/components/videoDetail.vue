<template >
  <div v-if = "video" class="col-md-8">
    <div class="embed-responsive embed-responsive-16by9">
      <iframe class="embed-responsive-item" :src = "videoUrl"></iframe>
    </div>
    <div class="details">
        <h4>{{video.snippet.title}}</h4>
        <p>{{video.snippet.description}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'videoDetail',
  props: ['video'],
  computed : {
    videoUrl () {
      const videoID = this.video.id.videoId;
      return `https://www.youtube.com/embed/${videoID}`;
    }
  }
}
</script>

<style>
.details {
  margin-top: 10px;
  padding: 10px;
  border: 1px solid black;
  border-radius: 4px;
}
</style>
