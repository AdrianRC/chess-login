<template>
  <div id="app">
    <authenticate></authenticate>
  </div>
</template>

<script>
import Authenticate from './components/Authenticate';

export default {
  name: 'app',
  components: {
    Authenticate,
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  background-color: rgb(70, 66, 64);
  width: 100%;
  height: 100%;
  margin: 0;
  padding-top: 85px;
}


html, body {
  height: 720px;
  width: 1300px;
  margin: 0;
  padding: 0;
}
</style>