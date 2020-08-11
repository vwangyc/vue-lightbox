<template>
  <div id="app">
    <div class="gallery">
      <div v-for="(image, index) in images" :key="index">
        <img class="images" alt="image" :src="require('@/assets/thumbnails/' + `${image.filename}`)"
            @click="openImage(image.filename)">
      </div>
    </div>
    <Lightbox ref="lightbox"/>
  </div>
</template>

<script>
import Lightbox from './components/Lightbox.vue'
import images from './images.js'

export default {
  name: 'App',
  components: {
    Lightbox,
  },
  data () {
    return {
      images,
    }
  },
  methods: {
    openImage(filename) {
      this.$refs.lightbox.showImage(filename)
    },
  }
}
</script>

<style>
.gallery {
  align-items: center;
  display: grid;
  grid-gap: 15px;
  grid-template-columns: repeat(3, 300px);
  height: 100vh;
  justify-content: center;
}

.images {
  cursor: pointer;
  height: 200px;
  width: 300px;
}
</style>
