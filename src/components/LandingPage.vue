<script setup>
import Header from './Header.vue';
import UserOptions from './UserOptions.vue';
import ResultComponent from './ResultComponent.vue'
import { reactive, onBeforeMount } from 'vue'

const data = reactive({
  showOverlay: false,
  userChoice: "",
  computerChoice: "",
  localScore: 0,
});

const possibleChoices = ['paper', 'scissors', 'rock']

onBeforeMount(() => {
  getComputerChoice()
  data.localScore = localStorage.getItem('setScore') ? localStorage.getItem('setScore') : 0;
})

function getComputerChoice() {
  data.computerChoice = possibleChoices[Math.floor(Math.random() * (2 - 0 + 1)) + 0]

}

function getScore(score) {
  data.localScore = Number(data.localScore) + 1
}


function showRules() {
  data.showOverlay = true
}
function closeRules() {
  data.showOverlay = false
}

function setChoice(val) {
  data.userChoice = val

}
function tryAgain(val) {
  data.userChoice = "",
    getComputerChoice()

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
    <Header :allScore="data.localScore" />

    <UserOptions v-if="!data.userChoice" @sendChoice="setChoice" />
    <ResultComponent v-else :computerChoice="data.computerChoice" :userChoice="data.userChoice" @tryAgain="tryAgain"
      @sendScore="getScore" />


    <div class="footer">
      <button @click="showRules()">Rules</button>
    </div>

  </div>
</template>
