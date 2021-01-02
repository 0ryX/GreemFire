<template>
  <div>
    <div class="title">Coins</div>
    <div class="items">
      <div class="item">
        <div class="name">Tezos:</div>
        <div class="value">${{ tezos }}</div>
        <canvas id="tezos"></canvas>
      </div>
       <div class="item">
        <div class="name">Burst:</div>
        <div class="value">${{ burst }}</div>
        <canvas id="burst"></canvas>
      </div>
       <div class="item">
        <div class="name">Cardano:</div>
        <div class="value">${{ ada }}</div>
        <canvas id="ada"></canvas>
      </div>
    </div>
    <canvas id="mac"></canvas>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        tezos: 0.0,
        ada: 0.0,
        burst: 0.0
      }
    },
    created () {
      const CoinMarketCap = require('coinmarketcap-api')
      const apiKey = '939ac68e-0bb6-4f25-9c37-fbc9afa82c6d'
      const client = new CoinMarketCap(apiKey)
      let that = this
      client.getQuotes({symbol: 'XTZ,ADA,BURST'}).then(data => {
        that.ada = data.data.ADA.quote.USD.price
        that.tezos = data.data.XTZ.quote.USD.price
        that.burst = data.data.BURST.quote.USD.price
      }).catch(console.error)
    },
    mounted () {
      var QRCode = require('qrcode')
      var tezos = document.getElementById('tezos')
      QRCode.toCanvas(tezos, `Tezos is $${this.tezos}`, function (error) {
        if (error) console.error(error)
        console.log('success!')
      })
      var ada = document.getElementById('ada')
      QRCode.toCanvas(ada, `Cardano is $${this.ada}`, function (error) {
        if (error) console.error(error)
        console.log('success!')
      })
      var burst = document.getElementById('burst')
      QRCode.toCanvas(burst, `Burst is $${this.burst}`, function (error) {
        if (error) console.error(error)
        console.log('success!')
      })
    }
  }
</script>

<style scoped>
  .title {
    color: #888;
    font-size: 18px;
    font-weight: initial;
    letter-spacing: .25px;
    margin-top: 10px;
  }

  .items { margin-top: 8px; }

  .item {
    display: flex;
    margin-bottom: 6px;
  }

  .item .name {
    color: #6a6a6a;
    margin-right: 6px;
  }

  .item .value {
    color: #35495e;
    font-weight: bold;
  }
</style>
