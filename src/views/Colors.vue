<template>
  <div class="colors">
    <p v-for="(p, index) in content" :key="p" :class="'p-'+index">{{ p }}</p>
    <div>
      <button class="button" @click="randomAll">Random All</button>
      <button @click="randomByItem">Random by item</button>
    </div>
  </div>
</template>
<script>
import { select, selectAll } from 'd3-selection'
export default {
  data: () => ({
    paragraphs: [1, 2, 3, 4, 5],
    content: [1, 2, 3, 4, 5].map(id => `Content ${id}`),
    colors: [
      'brown',
      'cadetblue',
      'chocolate',
      'olive',
      'cornflowerblue',
      'crimson',
      'darkcyan',
      'darkmagenta',
      'darkorange',
      'darkseagreen',
      'darkturquoise',
      'floralwhite',
      'gainsboro',
    ],
  }),
  mounted() {
    selectAll('p').style('color', 'blue')
  },
  methods: {
    getColor() {
      return this.colors[Math.floor(Math.random() * this.colors.length)]
    },
    randomAll() {
      selectAll('p').style('color', this.getColor())
      selectAll('p').style('background-color', this.getColor())
    },
    randomByItem() {
      this.paragraphs.forEach((p, index) => {
        select(`.p-${index}`).style('color', this.getColor())
        select(`.p-${index}`).style('background-color', this.getColor())
      })
    },
  },
}
</script>
<style lanng="scss">
p {
  transition: color 1s, background-color 1s;
  padding: 1rem;
  font-weight: bold;
}
</style>
