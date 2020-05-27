<template>
  <div>
    <Header/>
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoDetail :video="selectedVideo"></VideoDetail>
    <VideoList @videoSelect="onVideoSelect" :videos="videos"></VideoList>
  </div>
</template>

<script>
  import axios from 'axios';
  import Header from './components/Header';
  import SearchBar from './components/SearchBar';
  import VideoList from './components/VideoList';
  import VideoDetail from './components/VideoDetail';
  const API_KEY = 'AIzaSyAZgdTEORTr3vvLRatG16yQCXAZghPovPs';

  export default {
    name: 'App',
    components: {
      Header,
      SearchBar,
      VideoList,
      VideoDetail
    },
    data() {
      return { videos: [], selectedVideo: null };
    },
    methods: {
      onVideoSelect(video) {
        this.selectedVideo = video;
      },
      onTermChange(searchTerm) {

        axios.get('https://www.googleapis.com/youtube/v3/search', {
          params: {
            key: API_KEY,
            type: 'video',
            part: 'snippet',
            q: searchTerm
          }
        }).then(response => {
          this.videos = response.data.items;
        });
      }
    }
  }
</script>

<style>
  * { box-sizing: border-box; }

  body {
    margin: 0;
    font-family: 'Roboto', sans-serif;
    min-height: 100vh;
    background-color: #212121;
  }

  .constraint {
    padding-left: 15px;
    padding-right: 15px;
    max-width: 1020px;
    margin-right: auto;
    margin-left: auto;
  }
</style>