<template>
  <div id="app">
    <ZigBoard v-bind:title="title" v-bind:sounds="sounds"/>
  </div>
</template>

<script>
import ZigBoard from './components/ZigBoard.vue'
import soundData from './assets/sound-data.json'
export default {
  name: 'app',
  components: {
    ZigBoard
  },
  data: ()=>({
    title: 'ZigBoard',
    sounds: soundData
  })
}
</script>

<style>
html{
  padding: 0;
  margin: 0;
  background: #46c9e5;
}
body{
  margin: 0;
  padding: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background: #ffffff;
  margin: 8px;
  padding: 20px;
  border-radius: 4px;
  box-shadow: 0 4px rgba(0,0,0,.10);
}
</style>
