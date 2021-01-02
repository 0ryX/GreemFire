<template>
  <div>
    <div class='title'>Download</div>
    <button v-on:click='download'>Download</button>
    <a href='#' id='download' download='screenshot.png'/></a>
  </div>
</template>

<script>
  import html2canvas from 'html2canvas'
  export default {
    methods: {
      download () {
        html2canvas(document.body).then(canvas => {
          let url = canvas.toDataURL('image/png')
          let nindown = document.getElementById('download')
          nindown.href = url
          nindown.click()
        })
      }
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
