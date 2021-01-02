<template>
  <div id="app">
    <full-name></full-name>
    <system-information></system-information>
    <mac></mac>
    <coins></coins>
    <download></download>
    <a href='https://github.com/0ryX' target="_blank">Github</a>
    <a href='mailto:seth.sampson1987@gmail.com' target="_blank">Email</a>
    <a href='https://docs.google.com/document/d/1tQBawvpt221cVuBHEm4HFqksIst0hGJe2VU0j4fbFkY/edit?usp=sharing' target="_blank">Resume</a>
  </div>
</template>
<script>
  import FullName from '@/components/FullName'
  import SystemInformation from './components/LandingPage/SystemInformation'
  import Mac from './components/LandingPage/Mac'
  import Coins from './components/LandingPage/Coins'
  import Download from './components/LandingPage/Download'
  export default {
    name: 'greenfire',
    components: {
      FullName,
      SystemInformation,
      Mac,
      Coins,
      Download
    }
  }
</script>
<style>
  /* CSS */
</style>

