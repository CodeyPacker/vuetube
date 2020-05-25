<template>
  <ul>
    <VideoListItem
      v-for="video in videos"
      :video="video"
      :key="video.etag"
      @videoSelect="onVideoSelect"
    >
    </VideoListItem>
  </ul>
</template>

<script>
  import VideoListItem from './VideoListItem'
  export default {
    name: 'VideoList',
    components: {
      VideoListItem
    },
    props: ['videos'],
    methods: {
      onVideoSelect(video) {
        // emit the same event up to the App component
        this.$emit('videoSelect', video)
      }
    }
  }
</script>

<style>

</style>