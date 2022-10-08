<template>
  <div class="card">
    <h2>Before conversion - YouTube URL</h2>
    <hr>
    <input type="text" v-model="sourceUrl">
    <div class="mt">
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
      this.$emit('clearYoutubeInfo')
    },
    async paste() {
      this.sourceUrl = await navigator.clipboard.readText()
    },
    convert() {
      // https://www.youtube.com/watch?v={id}
      // https://youtu.be/{id}
      try {
        const url = new URL(this.sourceUrl)
        const params = url.searchParams
        let id = '';
        if (url.origin === 'https://www.youtube.com' && params.get('v')) {
          id = params.get('v')
        } else if (url.origin === 'https://youtu.be') {
          id = url.pathname.substr(1, url.pathname.length)
        } else {
          alert('ERROR: Not a YouTube URL.')
          return
        }
        const thumbnailUrl = `https://img.youtube.com/vi/${id}/0.jpg`
        const markdownTxt = `[![](${thumbnailUrl})](https://www.youtube.com/watch?v=${id})`
        this.$emit('pushYoutubeInfo', {markdownTxt: markdownTxt, thumbnailUrl: thumbnailUrl})
      } catch(e) {
        console.error(e)
        alert('ERROR: Please check the URL you entered.')
      }
    }
  }
}
</script>

<style scoped>
</style>
