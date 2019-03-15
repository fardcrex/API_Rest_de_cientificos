<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
   
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'home',
  components: {
    
  }
}
</script>
<style lang="scss">
  html {
    box-sizing: border-box;
    font-family: 'Chalet', sans-serif;
    font-size: 16px;
  }
  
  h1,h2,h3,*,
  *:after,
  *:before {
    box-sizing: inherit;
    margin: 0;
    padding: 0;
  }
  
  @import "config/variables";
  h1{
    margin: 0;
  }
  
</style>