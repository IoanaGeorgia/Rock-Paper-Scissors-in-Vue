<script setup>
import { ref, reactive, computed, onMounted } from 'vue'


   const props =  defineProps({
      computerChoice: { type: String, required: true },
      userChoice: { type: String, required: true },
   })

   const styles ={
    'rock':{
        class:'rockBg',
        img:'../images/icon-rock.svg'
    },
    'paper':{
        class:'paperBg',
        img:'../images/icon-paper.svg'
    },
    'scissors':{
        class:'scissorsBg',
        img:'../images/icon-scissors.svg'
    }
   }

const userChoiceImage =  new URL(styles[props.userChoice].img, import.meta.url)
const computerChoiceImage =  new URL(styles[props.computerChoice]?.img, import.meta.url)

const userChoiceClass=styles[props.userChoice].class
const computerChoiceClass=styles[props.computerChoice]?.class

// const computerChoiceImage = new URL(styles[props.computerChoice].img, import.meta.url)

// function imageSourceComputer() {
//     // var images = require.context("../images/image-rules.svg")
//     return "../images/image-rules.svg"
// }

</script>
<template>
    <div class="userWrapper">
        <div class="resultInnerWrapper">
            <div class="userChoiceWrapper">
                <p>You picked</p>
                <div class="outerUserChoice" :class="userChoiceClass">
                    <div class="innerUserChoice">
                        <img :src="userChoiceImage">
            
                    </div>
                </div>
            </div>

            <div class="userChoiceWrapper">
                <p>The house picked</p>
                <div class="outerUserChoice" :class="computerChoiceClass">
                    <div class="innerUserChoice">
                        <img :src="computerChoiceImage">
                    </div>
                </div>
            </div>

        </div>
    </div>
</template>

<style scoped>

</style>
