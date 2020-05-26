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
  /* I could do this in a lot less code without using the 16/9 ratio.... */
  .video-title {
    color: #fff;
    padding: 15px;
    display: block;
  }

  .video-wrapper {
    background-color: #000;
    margin-bottom: 20px;
  }

  @media screen and (max-width: 700px) {
    .video-wrapper { position: relative; }

    .video {
      list-style-type: none;
      /* 16/9 */
      width: 100%;
      padding-top: 56.25%;
      margin-bottom: 65px;
    }

    .thumbnail {
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
    }
  }

  @media screen and (min-width: 700px) {
    .video-wrapper {
      width: 100%;
      max-width: 47%;
      margin-bottom: 35px;
    }

    .video {
      display: flex;
      flex-direction: column;
      justify-content: center;
    }

    .video-wrapper:nth-child(odd) { margin-right: 20px; }
  }
</style>