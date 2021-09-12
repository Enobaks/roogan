<template>
  <div id="home">
    <Navbar />
    <Body />

    
  </div>
  
</template>

<script>
import Navbar from './components/Navbar.vue'
import Body from './components/Body.vue'
export default {
  name: 'App',
  components: {Navbar, Body}
}

</script>

<style lang="scss">
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
#app {
  // font-family: Avenir, Helvetica, Arial, sans-serif;
  font-family: "Raleway", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

  @font-face {
  font-family: 'Raleway';
  src: url(./assets/fonts/Raleway-Regular.ttf) format('ttf');
  font-style: normal;
  font-weight: 400;
}

@font-face {
  font-family: 'Raleway';
  src: url(./assets/fonts/Raleway-Medium.ttf) format('ttf');
  font-style: normal;
  font-weight: 500;
}

@font-face {
  font-family: 'Raleway';
  src: url(./assets/fonts/Raleway-SemiBold.ttf) format('ttf');
  font-style: normal;
  font-weight: 600;
}

@font-face {
  font-family: 'Raleway';
  src: url(./assets/fonts/Raleway-Bold.ttf) format('ttf');
  font-style: normal;
  font-weight: 700;
}

@font-face {
  font-family: 'Raleway';
  src: url(./assets/fonts/Raleway-ExtraBold.ttf) format('ttf');
  font-style: normal;
  font-weight: 800;
}

@font-face {
  font-family: 'Raleway';
  src: url(./assets/fonts/Raleway-Black.ttf) format('ttf');
  font-style: normal;
  font-weight: 900;
}
}

#home {
  width: 100%;
  height: auto;

  
}
</style>
