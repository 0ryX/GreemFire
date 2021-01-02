<template>
  <div>
    <div class="title">System Information</div>
    <div class="items">
      <div class="item">
        <div class="name">IP:</div>
        <div class="value">{{ ip }}</div>
      </div>
      <div class="item">
        <div class="name">RAM:</div>
        <div class="value">{{ ram }}</div>
      </div>
      <div class="item">
        <div class="name">Platform:</div>
        <div class="value">{{ platform }}</div>
      </div>
    </div>
    <canvas id="system"></canvas>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        ip: '',
        ram: '',
        platform: ''
      }
    },
    mounted () {
      const os = require('os')
      this.ip = os.networkInterfaces().wlp5s0[0].address
      this.ram = os.totalmem()
      this.platform = os.platform()
      const system = `IP is ${this.ip} RAM is ${this.ram} OS is ${this.platform}`
      var QRCode = require('qrcode')
      var canvas = document.getElementById('system')
      QRCode.toCanvas(canvas, system, function (error) {
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
