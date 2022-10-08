<template>
  <div class="card">
    <h2>Before conversion - YouTube Url</h2>
    <hr>
    <input type="text" v-model="sourceUrl">
    <div style="margin-top: 20px">
      <button @click="clear()">clear</button>
      <button @click="paste()">paste</button>
      <button @click="convert()">convert</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BeforeConversion',
  data() {
    return {
      sourceUrl: ''
    }
  },
  methods: {
    clear() {
      this.sourceUrl = ''
      this.$emit('clearMarkdownTxt')
    },
    async paste() {
      this.sourceUrl = await navigator.clipboard.readText()
    },
    convert() {
      // https://www.youtube.com/watch?v={id}
      // https://youtu.be/{id}
      const src = this.sourceUrl
      console.log(src)
      // [![](https://img.youtube.com/vi/LIlZCmETvsY/0.jpg)](https://www.youtube.com/watch?v=LIlZCmETvsY)
      const markdownTxt = '[![](https://img.youtube.com/vi/LIlZCmETvsY/0.jpg)](https://www.youtube.com/watch?v=LIlZCmETvsY)'
      this.$emit('pushMarkdownTxt', {markdownTxt: markdownTxt})
    }
  }
}
</script>

<style scoped>
</style>
