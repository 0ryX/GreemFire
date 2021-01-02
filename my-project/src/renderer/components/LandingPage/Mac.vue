<template>
  <div>
    <div class="title">Mac Information</div>
    <div class="items">
      <div class="item">
        <div class="name">Mac Address:</div>
        <div class="value">{{ mac }}</div>
      </div>
    </div>
    <canvas id="mac"></canvas>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        mac: ''
      }
    },
    mounted () {
      const os = require('os')
      this.mac = os.networkInterfaces().wlp5s0[0].mac
      const mac = `Mac address is ${this.mac}`
      var QRCode = require('qrcode')
      var canvas = document.getElementById('mac')
      QRCode.toCanvas(canvas, mac, function (error) {
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
