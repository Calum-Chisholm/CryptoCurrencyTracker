<template lang="html">
  <!-- <GChart
    type="PieChart"
    :data='formattedData'
    :options='chartOptions'
    class="chart"/> -->
    <ul>
      <li v-for="item in cryptoStats">{{item}}</li>
    </ul>
</template>

<script>
import { GChart } from 'vue-google-charts'

export default {
  name: 'crypto-chart',
  props: ['cryptoStats'],
  components: {

  }
}


</script>

<style lang="css" scoped>
</style>
