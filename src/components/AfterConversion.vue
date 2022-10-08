<template>
  <div class="card">
    <h2>After conversion - Markdown</h2>
    <hr>
    <input type="text" v-model="markdownTxt">
    <div style="margin-top: 20px">
      <button @click="copy()">copy</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AfterConversion',
  data() {
    return {
      markdownTxt: ''
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
