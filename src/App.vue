<template>
 <div>
   <Dialogs/>
   <button @click="dialog.alert('onClickonClickonClickonClickonClickonClickonClickonClickonClick')">dialog</button>
   <button @click="dialog.confirm('1')">dialog</button>
 </div>
</template>

<script>
import { dialog } from "./components/dialog.js"
import Dialogs from './components/Dialogs.vue'
export default {
  components: {Dialogs},
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
