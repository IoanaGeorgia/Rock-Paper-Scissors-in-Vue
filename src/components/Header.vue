<script setup>
import { ref, reactive, computed, onMounted } from 'vue'

   const props =  defineProps({
      allScore: {  required: true },
   })
</script>

<template>
  <div class="headerWrapper">
    <div class="innerHeaderWrapper">
      <div class="headerTitle">
        <div>Rock</div>
        <div>Paper</div>
        <div>Scissors</div>
      </div>
      <div class="scoreWrapper">
          <p>Score</p>
          <p class="score">{{ props.allScore}}</p>
      </div>
    </div>

</div>
</template>
