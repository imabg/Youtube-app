<template>

    <ul class = "list-group col-md-4">
      <VideoListItem v-for = "video in videos"
        :video = "video"
        :key = "video.etag"
        @videoSelect = "onVideoSelect"
      > </VideoListItem>
    </ul>
</template>

<script>
import VideoListItem from './videoListItem';
export default {
    name: 'VideoList',
      props: ['videos'],
    components: {
      VideoListItem
    },
    methods: {
      onVideoSelect(video) {
        this.$emit('videoSelect', video);
      }
    }
}
</script>

<style>

</style>
