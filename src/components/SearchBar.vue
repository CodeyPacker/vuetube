<template>
  <div class="constraint">
    <input @input="onInput" class="searchbar"/>
  </div>
</template>

<script>
  export default {
    name: 'SearchBar',
    methods: {
      onInput: function(event) {
        this.$emit('termChange', event.target.value);
      }
    }
  };
</script>

<style>
  .searchbar {
    width: 100%;
    border: 0;
    background-color: #121212;
    color: #fff;
    text-align: center;
    font-size: 22px;
    padding: 15px;
    border-radius: 10px;
    margin-bottom: 20px;
  }

  @media screen and (min-width: 700px) {
    .searchbar { text-align: left; }
  }
</style>