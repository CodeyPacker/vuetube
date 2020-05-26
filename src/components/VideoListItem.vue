<template>
  <div class="video-wrapper">
  <!-- not semantic | refactor -->
    <li @click="onVideoSelect" class="video">
      <img :src="thumbnailUrl" class="thumbnail"/>
    </li>
    <span class="video-title">{{video.snippet.title}}</span>
  </div>
</template>

<script>
  export default {
    name: 'VideoListItem',
    props: ['video'],
    computed: {
      thumbnailUrl() {
        return this.video.snippet.thumbnails.high.url;
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

<style scope>
  @media screen and (max-width: 500px) {
    .video-wrapper {
      position: relative;
    }

    .video {
      list-style-type: none;
      /* 16/9 */
      width: 100%;
      padding-top: 56.25%;
      margin-bottom: 65px;
    }

    .thumbnail {
      margin-right: 15px;
      /* 16/9 */
      position: absolute;
      top: 0;
      left: 0;
      bottom: 0;
      right: 0;
      width: 100%;
      height: 100%;
    }

    .video-title {
      z-index: 2;
      position: absolute;
      bottom: -45px;
      left: 0;
      right: 0;
      background-color: #000;
      color: #fff;
      padding: 15px;
    }
  }

  @media screen and (min-width: 500px) {
    .video-wrapper {
      flex-basis: 50%;
    }

    .video {
      display: flex;
      flex-direction: column;
      justify-content: center;
    }

    .video-wrapper:nth-child(odd) {
      padding-right: 20px;
    }
  }
</style>