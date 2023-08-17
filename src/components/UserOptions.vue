<script setup>

const emit = defineEmits(['sendChoice'])

function getChoice(choice) {
  emit('sendChoice', choice)

}
</script>

<template>
  <div class="userWrapper">
    <div class="userInnerWrapper">
      <img src="../images/bg-triangle.svg" />
      <div @click="getChoice('paper')" class="paper outerOptionWrapper">
        <div class="optionSelection">
          <img src="../images/icon-paper.svg" />
        </div>
      </div>
      <div @click="getChoice('scissors')" class="scissors outerOptionWrapper">
        <div class="optionSelection">
          <img src="../images/icon-scissors.svg" />
        </div>
      </div>
      <div @click="getChoice('rock')" class="rock outerOptionWrapper">
        <div class="optionSelection">
          <img src="../images/icon-rock.svg" />
        </div>
      </div>
    </div>
  </div>
</template>


