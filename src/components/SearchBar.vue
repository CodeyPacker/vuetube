<template>
  <form @submit.prevent="onSubmit" class="constraint searchbar-container">
    <input class="searchbar"/>
    <button class="search-button"><img class="search-icon" src="../images/search-icon.svg" /></button>
  </form>
</template>

<script>
  export default {
    name: 'SearchBar',
    methods: {
      onSubmit: function(event) {
        this.$emit('termChange', event.target.children[0].value);
      }
    }
  };
</script>

<style>
  .searchbar-container {
    display: flex;
  }

  .searchbar {
    width: 100%;
    border: 0;
    background-color: #121212;
    color: #fff;
    text-align: center;
    font-size: 22px;
    padding: 15px;
    border-radius: 10px 0 0 10px;
    margin-bottom: 20px;
  }

  .search-button {
    background-color: #121212;
    border: 0;
    padding: 15px;
    border-radius: 0 10px 10px 0;
    margin-bottom: 20px;
  }

  @media screen and (min-width: 700px) {
    .searchbar { text-align: left; }

    .search-icon {
      width: 26px;
      height: 26px;
      fill: #fff;
    }
  }
</style>