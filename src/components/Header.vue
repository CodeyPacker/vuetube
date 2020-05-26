<template>
  <div class="constraint">
    <div class="header">
      <div class="logo-wrapper">
        <img src="../images/vue-logo.png" class="logo" alt="Vue logo"/>
        <span class="vuetube">ueTube</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header"
}
</script>

<style scope>
  .header { padding: 40px 15px; }

  .logo-wrapper {
    display: flex;
    justify-content: center;
  }

  .logo { max-width: 40px; }

  .vuetube {
    color: white;
    font-size: 30px;
    line-height: 33px;
  }

  @media screen and (min-width: 768px) {
    .logo-wrapper { justify-content: flex-start; }
  }

</style>