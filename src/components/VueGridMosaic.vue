<template>
  <div class="vue-grid-mosaic" v-bind="$attrs" :style="gridTemplate">
    <div v-for="(image, key) in images" :key="key" :class="`vue-grid-mosaic__tile-${key + 1}`" :style="getTileStyles(key)">
      <img :src="image.src" :class="`vue-grid-mosaic__image vue-grid-mosaic__image--${key}`" :style="imageStyles">
    </div>
  </div>
</template>

<script>
export default {
  props: {
    images: {
      type: Array,
      default: () => []
    },

    //Sets the amount of columns the grid will have
    templateColumns: {
      type: String,
      default: '50px repeat(6, 1fr)'
    },

    //Sets the amount of rows the grid will have
    templateRows: {
      type: String,
      default: 'repeat(2, 1fr)'
    },

    //Sets the space between the columns and rows
    gridGap: {
      type: String,
      default: '1rem'
    },

    //Sets the space between the columns
    gridColumnGap: {
      type: String,
      default: '1rem'
    },

    //Sets the space between the rows
    gridRowGap: {
      type: String,
      default: '1rem'
    },

    imageRadius: {
      type: String,
      default: '0'
    },

    objectFit: {
      type: String,
      default: 'cover'
    },

    borders: {
      type: String,
      default: 'none'
    }
  },

  computed: {
    gridTemplate () {
      return `
        display: grid;
        padding: 20px;
        grid-template-columns: ${this.templateColumns};
        grid-template-rows: ${this.templateRows};
        grid-gap: ${this.gridGap};
        column-gap: ${this.gridColumnGap};
        row-gap: ${this.gridRowGap};
      `
    },

    imageStyles () {
      return `
        width: 100%;
        height: 100%;
        border-radius: ${this.imageRadius};
        border: ${this.borders};
        object-fit: ${this.objectFit}
      `
    }
  },

  methods: {
    getTileStyles (key) {
      console.log(this.images)
      return `
        grid-column: ${this.images[key].gridColumn}; 
        grid-row: ${this.images[key].gridRow};
        `
    }
  }
}
</script>