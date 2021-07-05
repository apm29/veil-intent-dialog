<template>
  <div>
    <VeilIntentDialog/>
    <button @click="dialog.alert('onClickonClickonClickonClickonCliXXXXXXXckonClickonClickonClickonClick')">dialog</button>
    <button @click="dialog.confirm('1')">dialog</button>
  </div>
</template>

<script>
import { VeilIntentDialog,dialog } from '@/entry.esm'
export default {
  components: { VeilIntentDialog },
  data(){
    return {
      dialog
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
