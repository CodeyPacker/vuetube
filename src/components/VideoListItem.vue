<template>
  <li @click="onVideoSelect">
    <img :src="thumbnailUrl" />
    {{video.snippet.title}}
  </li>
</template>

<script>
  export default {
    name: 'VideoListItem',
    props: ['video'],
    computed: {
      thumbnailUrl() {
        return this.video.snippet.thumbnails.default.url;
      }
    },
    methods: {
      onVideoSelect() {
        // Sends event (containing the clicked video) up to the parent -> VideoList
        this.$emit('videoSelect', this.video);
      }
    }
  }
</script>