<script setup>
import Header from './Header.vue';
import { ref, reactive, computed } from 'vue'
defineProps({
  msg: {
    type: String,
    required: true
  }
})

  const data = reactive({ showOverlay: false });
const cat ="small little cat"

function showRules(){
  this.data.showOverlay = true
}
function closeRules(){
  this.data.showOverlay = false
}
</script>

<template>
<div v-if="data.showOverlay" class="overlayWrapper">
  <div class="rulesBackground">
    <div class="rulesHeader">
      <span>Rules</span>
      <img @click='closeRules()' src="../images/icon-close.svg">
    </div>
  <img src="../images/image-rules.svg">
  </div>
</div>

<div class="normalWrapper">
<Header/>
I love my {{ cat }}


<div class="footer">
  <button @click="showRules()">Rules</button>
</div>

</div>
</template>

<style scoped>

</style>
