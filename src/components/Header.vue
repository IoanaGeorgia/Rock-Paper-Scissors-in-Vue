<script setup>

const score = localStorage.getItem('setScore') ? localStorage.getItem('setScore') : 0;

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
          <p class="score">{{ score }}</p>
      </div>
    </div>

</div>
</template>
