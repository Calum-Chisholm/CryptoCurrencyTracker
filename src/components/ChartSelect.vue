<template lang="html">
  <div class="select">
    <h1>Crypto Charts</h1>
    <p>Please choose your type of Chart:</p>
    <select v-on:change="handleSelectedChart" v-model="selectedChart">
    </option>
    <option value="LineChart" selected="selected">Line Graph</option>
    <option value="Table">Table</option>
    <option value="ColumnChart">Column Chart</option>
    <option value="BarChart">Bar Chart</option>
  </select>
</div>
</template>

<script>
import {eventBus} from '@/main.js';

export default {
  name: 'chart-select',
  data() {
    return {
      selectedChart: null
    }
  },
  methods: {
    handleSelectedChart() {
      eventBus.$emit('selected-chart', this.selectedChart)
    }
  }
}
</script>

<style lang="css" scoped>
 .select {
   padding-bottom: 5%;
 }
</style>
