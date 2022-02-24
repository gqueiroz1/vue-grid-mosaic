<template>
  <div id="app">
    <div class="vue-grid-mosaic-wrapper">
      <vue-grid-mosaic :template-columns="templateColumns" :template-rows="templateRows" image-radius="10px" borders="solid 1px grey" :images="imagesList" grid-gap="2rem"/>
    </div>
  </div>
</template>

<script>
import VueGridMosaic from './components/VueGridMosaic.vue'

export default {
  components: { VueGridMosaic },

  name: 'App',

  computed: {
    templateColumns () {
      return `20% 100px repeat(2, 1fr)`
    },

    templateRows () {
      return `
        20% 100px repeat(8, 1fr)
      `
    },

    imagesList () {
      return [
        {
          src: 'https://picsum.photos/999',
          gridColumn: '1',
          gridRow: '1'
        },
        {
          src: 'https://picsum.photos/1000',
          gridColumn: '2',
          gridRow: '2'
        },
        {
          src: 'https://picsum.photos/800',
          gridColumn: '3',
          gridRow: '3'
        }         
      ]
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin: 60px 30px;
  color: #2c3e50;
  max-width: 100%;
}

p {
  font-weight: bold;
}

.vue-grid-mosaic-wrapper {
  margin: auto;
  width: 50%;
  padding: 15px;
  max-width: 100%;
  background-color: #c3c3c3;
}
</style>
