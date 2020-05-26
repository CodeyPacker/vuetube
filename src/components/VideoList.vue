<template>
  <div class="constraint">
    <ul class="video-list">
      <VideoListItem
        v-for="video in videos"
        :video="video"
        :key="video.etag"
        @videoSelect="onVideoSelect"
      >
      </VideoListItem>
    </ul>
  </div>
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

<style scope>
  .video-list {
    padding-left: 0;
  }

  @media screen and (min-width: 500px) {
    .video-list {
      display: flex;
      flex-wrap: wrap;
    }
  }
</style>