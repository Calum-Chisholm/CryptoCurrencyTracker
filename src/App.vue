<template lang="html">
  <crypto-chart :cryptoStats="this.cryptoStats"></crypto-chart>
</template>

<script>
import CryptoChart from '@/components/CryptoChart'
import {eventBus} from '@/main.js';

export default {
  name: 'app',
  data() {
    return {
      cryptoStats: null
    }
  },
  mounted(){
    fetch('https://api.coingecko.com/api/v3/coins/markets?vs_currency=gbp&order=market_cap_desc&per_page=100&page=1&sparkline=false&price_change_percentage=1h%2C24h%2C7d')
    .then(res => res.json())
    .then(data => this.cryptoStats = data);
  },
  components: {
    'crypto-chart': CryptoChart
  }
}
</script>

<style lang="css">
body {
  background:linear-gradient(180deg, LightCoral 0%, FireBrick 100%);
  text-align: center;
  font-family: Helvetica;
}


</style>
