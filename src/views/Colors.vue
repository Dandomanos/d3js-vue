<template>
  <div class="colors">
    <p v-for="(p, index) in content" :key="`p-${index}`" :class="'p-'+index">{{ p }}</p>
    <div class="toolbar">
      <label>Selected parapraph</label>
      <select v-model="selected">
        <option v-for="(opt, index) in content" :key="`o-${opt}`" :value="index">{{ opt }}</option>
      </select>
      <button @click="updateSelected">Selected</button>
    </div>
    <div class="toolbar">
      <button class="button" @click="randomAll">Random All</button>
      <button @click="randomByItem">Random by item</button>
      <button @click="zebra">Zebra</button>
      <button @click="delay">Delay</button>
    </div>
  </div>
</template>
<script>
import { select, selectAll } from 'd3-selection'
import 'd3-transition'
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
    selected: 0,
  }),
  mounted() {
    selectAll('p').style('color', 'blue')
  },
  methods: {
    getColor() {
      return this.colors[Math.floor(Math.random() * this.colors.length)]
    },
    getZebra(i) {
      return i % 2 ? '#fff' : '#eee'
    },
    randomAll() {
      selectAll('p')
        .style('color', this.getColor())
        .style('background-color', this.getColor())
    },
    randomByItem() {
      selectAll('p')
        .style('color', () => this.getColor())
        .style('background-color', () => this.getColor())
    },
    zebra() {
      selectAll('p')
        .style('color', () => '#474747')
        .style('background-color', (c, i) => this.getZebra(i + 1))
    },
    delay() {
      selectAll('p')
        .transition()
        .duration(750)
        .delay((d, i) => i * 100)
        .style('background-color', this.getColor())
        .style('color', this.getColor())
    },
    updateSelected() {
      select(`.p-${this.selected}`)
        .style('color', this.getColor())
        .style('background-color', this.getColor())
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
.toolbar {
  display: flex;
}
</style>
