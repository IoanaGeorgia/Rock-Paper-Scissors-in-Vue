<script setup>
import Header from './Header.vue';
defineProps({
  msg: {
    type: String,
    required: true
  }
})

const cat ="small little cat"
</script>

<template>
<div class="overlayWrapper">
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
