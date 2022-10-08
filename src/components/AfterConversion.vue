<template>
  <div class="card">
    <h2>After conversion - Markdown</h2>
    <hr>
    <input type="text" v-model="markdownTxt">
    <div class="mt">
      <button @click="copy()">copy</button>
    </div>
    <div class="mt" v-if="thumbnailUrl !== ''">
      <img src="https://img.youtube.com/vi/LIlZCmETvsY/0.jpg">
    </div>
  </div>
</template>

<script>
export default {
  name: 'AfterConversion',
  data() {
    return {
      markdownTxt: '',
      thumbnailUrl: 'tmp'
    }
  },
  methods: {
    copy() {
      navigator.clipboard.writeText(this.markdownTxt)
    }
  }
}
</script>

<style scoped>
</style>
