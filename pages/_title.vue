<template>
  <div class="container">
    <div>
      <h1 class="title">chorus-contest</h1>
      <p>{{ song.title }}</p>
      <p>{{ song.writer }}</p>
      <p>{{ song.composer }}</p>
      <p>{{ song.arranger }}</p>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  async asyncData({ $content }) {
    const songs = await $content('songs').fetch()
    return { songs }
  },
  computed: {
    song() {
      return this.$data.songs.body.find(
        (song: any) => song.title === this.$route.params.title
      )
    },
  },
})
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
