<template>
  <div v-if="video">
    <iframe :src="videoUrl"/>
    <div class="details">
      <h4 class="title">{{ video.snippet.title }}</h4>
      <p>{{ video.snippet.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'VideoDetail',
  props: ['video'],
  computed: {
    videoUrl() {
      const { videoId } = this.video.id;
      return `https://youtube.com/embed/${videoId}`;
    }
  }
}
</script>

<style scoped>
  .details {
    padding-top: 15px;
    padding-bottom: 15px;
    color: #fff;
  }

  .title { margin-bottom: 15px; }
</style>