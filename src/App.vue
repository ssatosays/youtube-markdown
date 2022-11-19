<template>
  <before-conversion
    ref="bfConversion"
    @clearYoutubeInfo="clearYoutubeInfo"
    @pushYoutubeInfo="pushYoutubeInfo"
  ></before-conversion>
  <after-conversion
    ref="afConversion"
  ></after-conversion>
  <footer>
    <div>
      <a href="https://github.com/ssatosays/youtube-markdown">ssatosays/youtube-markdown</a>
    </div>
  </footer>
</template>

<script>
import BeforeConversion from './components/BeforeConversion.vue'
import AfterConversion from './components/AfterConversion.vue'

export default {
  name: 'App',
  components: {
    'before-conversion': BeforeConversion,
    'after-conversion': AfterConversion
  },
  data() {
    return {
    }
  },
  methods: {
    clearYoutubeInfo(){
      this.$refs.afConversion['markdownTxt'] = ''
      this.$refs.afConversion['thumbnailUrl'] = ''
    },
    pushYoutubeInfo(data) {
      this.$refs.afConversion['markdownTxt'] = data.markdownTxt
      this.$refs.afConversion['thumbnailUrl'] = data.thumbnailUrl
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 40px;
}
h2 {
  margin-top: 20px;
  margin-bottom: 10px;
}
hr {
  color: #d9d9d9;
}
input {
  background: #f2f2f2;
  border-radius: 5px;
  border-style: solid;
  border-width: 1px;
  border-color: #d9d9d9;
  font-size: 1rem;
  padding: 0.5rem;
  width: 95%;
}
input:focus {
  outline-color: #42b883;
}
button {
  font-size: 1rem;
  margin-left: 5px;
  margin-right: 5px;
}
img {
  width: 320px;
  height: auto;
}
.card {
  background: #f2f2f2;
  border-radius: 5px;
  border-style: solid;
  border-width: 1px;
  border-color: #d9d9d9;
  margin-top: 20px;
  margin-left: 40px;
  margin-right: 40px;
  padding: 10px;
}
.mt {
  margin-top: 20px;
}
footer div {
  margin-top: 50px;
  text-align: center;
}
footer div a {
  color: inherit;
  text-decoration: none;
}
</style>
