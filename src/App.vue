<template>
  <div id="app">
    <h1>Vue-chartkick</h1>
    <h2>Line Chart</h2>
    <line-chart :data="lineChartData"></line-chart>
    <h2>Column Chart</h2>
    <column-chart :data="columnChartData" ytitle="Km/h"></column-chart>
    <h2>Bar Chart</h2>
    <bar-chart :data="barChartData"></bar-chart>
    <h2>Area Chart</h2>
    <area-chart :data="areaChartData"></area-chart>

    <!-- infinite loader -->
    <h2>Infinite Loader</h2>
    <InfiniteLoader />
  </div>
</template>

<script>
import InfiniteLoader from './components/VueInfifniteLoader.vue'
export default {
  name: 'App',
  components: {
    InfiniteLoader
  },
  data() {
    return {
      lineChartData: {
        '2021-05-13': 2,
        '2021-05-14': 5,
        '2021-05-20': 7
      },
      columnChartData: [
        ['00h', 32],
        ['01h', 46], 
        ['02h', 28],
        ['03h', 50],
        ['04h', 60],
        ['05h', 33],
        ['06h', 68],
        ['07h', 80],
        ['08h', 28],
        ['09h', 28],
        ['10h', 28],
        ['11h', 28],
        ['12h', 28],
        ['13h', 28]
      ],
      barChartData: [
        ['Walk', 32], 
        ['Run', 1492]
      ],
      areaChartData: {
        '2021-01-01': 11,
        '2021-01-02': 6,
        '2021-03-20': 5,
        '2021-04-6': 14
      }
    }
  }
}
</script>

<style>
#app {
  padding: 0 20px 20px;
}
</style>
