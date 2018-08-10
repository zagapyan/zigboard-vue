<template>
  <div class="ZigBoard">
    <h1 ref="title">{{title}}<img :src="logo"/></h1>
    <ul class="sound-bytes">
      <li v-for="(sound, index) in sounds" :key="index">
        <a v-on:click="playSounds(sound.file)">{{ sound.name }}</a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "ZigBoard",
  props: ["title", "sounds"],
  data: () => ({
    logo: require("../assets/logo.png"),
    rotateActive: false
  }),
  methods: {
    playSounds: fileName => {
      const soundFile = require(`../assets/audio/${fileName}.mp3`);
      if (soundFile) {
        const audio = new Audio(soundFile);
        audio.play();
      }
    },
    rotate: ()=>{
      
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.ZigBoard{
  max-width: 980px;
  margin: 0 auto;
}
h1{
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px 0;
  color: #fff;
  font-size: 4rem;
}
@media(max-width: 980px){
  h1{
    font-size: 3rem
  }
}
@media(max-width: 400px){
  h1{
    font-size: 2rem
  }
}
h1 img{
  max-height: 80px;
  margin-left: 40px;
  width: auto;
  transition: .5s transform ease-in-out;
}
h1 img:hover{
  transform: rotate(360deg);
}
ul.sound-bytes {
  list-style-type: none;
  padding: 0;
  display: grid;
  grid-gap: 20px 20px;
  grid-template-columns: repeat(4, 1fr);
}
@media(max-width: 980px){
  ul.sound-bytes {
    grid-template-columns: repeat(2, 1fr);
  }
}
@media(max-width: 400px){
  ul.sound-bytes {
    grid-template-columns: repeat(1, 1fr);
  }
}
li {
  display: inline-block;
  box-sizing: border-box;
  border: 1px solid #000;
  width: 100%;
  border-radius: 2px;
  -webkit-text-decoration: none;
  text-decoration: none;
  background: linear-gradient(45deg, #d26ac2, #46c9e5);
  color: #1d2029;
  font-weight: 800;
  text-align: center;
}
a {
  box-sizing: border-box;
  color: #000;
  cursor: pointer;
  width: 100%;
  height: 100%;
  display: inline-flex;
  text-align: center;
  padding: 60px 20px;
  font-size: 1rem;
  justify-content: center;
}
</style>
