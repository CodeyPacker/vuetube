<template>
  <div>
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoList @videoSelect="onVideoSelect" :videos="videos"></VideoList>
  </div>
</template>

<script>
  import axios from 'axios';
  import SearchBar from './components/SearchBar';
  import VideoList from './components/VideoList';
  const API_KEY = 'AIzaSyAZgdTEORTr3vvLRatG16yQCXAZghPovPs';

  export default {
    name: 'App',
    components: {
      SearchBar,
      VideoList
    },
    data() {
      return { videos: [] };
    },
    methods: {
      onVideoSelect(video) {
        console.log(video);
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