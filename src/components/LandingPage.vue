<script setup>
import Header from './Header.vue';
import UserOptions from './UserOptions.vue';
import { ref, reactive, computed, onMounted } from 'vue'

  const data = reactive({ 
    showOverlay: false,
    userChoice:"",
    computerChoice:"" 
  });

  const possibleChoices = ['paper', 'scissors', 'rock']

    onMounted(() => {
    getComputerChoice()
})

  function getComputerChoice(){
     data.computerChoice =possibleChoices[Math.floor(Math.random() * (2 - 0 + 1)) + 0]
  }



function showRules(){
  this.data.showOverlay = true
}
function closeRules(){
  this.data.showOverlay = false
}

function setChoice(val){
  data.userChoice = val

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
<Header />

<UserOptions  @sendChoice="setChoice" />


<div class="footer">
  <button @click="showRules()">Rules</button>
</div>

</div>
</template>
