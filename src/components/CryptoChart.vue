<template lang="html">
  <div class="">
    <chart-select></chart-select>
    <GChart
    :type="selectedChart"
    :data='chartData'
    :options='chartOptions'
    class="chart"/>
  </div>
</template>

<script>
import {eventBus} from '@/main.js';
import { GChart } from 'vue-google-charts'
import ChartSelect from '@/components/ChartSelect'

export default {
  name: 'crypto-chart',
  props: ['cryptoStats'],
  components: {
    'chart-select': ChartSelect,
    GChart
  },
  data () {
    return {
      selectedChart: "LineChart",
      chartOptions: {
        width: 900,
        height: 500,
        chart: {
          title: 'Crypto Chart',
        }
      }
    }
  },
  mounted(){
    eventBus.$on('selected-chart', (chart) => {
      this.selectedChart = chart;
    })
  },
  computed: {
    chartData: function() {
      if (!this.cryptoStats) return;

      const smallData = this.cryptoStats.slice(0,10)
      const chartData = smallData.map((item) => {
        return [item.name, item.price_change_percentage_24h]
      })
      chartData.unshift(['Name', '24h Price Change Percentage'])
      return chartData
    }
  }
}



</script>

<style lang="css" scoped>
</style>
