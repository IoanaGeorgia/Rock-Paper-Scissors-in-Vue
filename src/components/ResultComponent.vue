<script setup>
import { reactive, computed, onMounted } from 'vue'
const emit = defineEmits(['tryAgain', 'sendScore'])


const props = defineProps({
    computerChoice: { type: String, required: true },
    userChoice: { type: String, required: true },
})
const data = reactive({
    showResult: false,
});
const styles = {
    'rock': {
        class: 'rockBg',
        img: './src/images/icon-rock.svg'
    },
    'paper': {
        class: 'paperBg',
        img: './src/images/icon-paper.svg'
    },
    'scissors': {
        class: 'scissorsBg',
        img: './src/images/icon-scissors.svg'
    }
}

onMounted(() => {
    setTimeout(() => {
        data.showResult = true;
    }, 1500); 
})


const userChoiceImage = new URL(styles[props.userChoice].img, import.meta.url)
const computerChoiceImage = new URL(styles[props.computerChoice]?.img, import.meta.url)

const userChoiceClass = styles[props.userChoice].class
const computerChoiceClass = styles[props.computerChoice]?.class

function updateLocalScore() {
    emit('sendScore', 1)
}

function tryAgain() {
    emit('tryAgain', true)
}
const result = computed(() => {
    if (props.userChoice === props.computerChoice) {
        return 'Equality'
    }
    if (props.userChoice == 'rock') {
        if (props.computerChoice == 'scissors') {
            updateLocalScore()
            if (localStorage.setScore) {
                localStorage.setScore = Number(localStorage.setScore) + 1
            } else {
                localStorage.setItem('setScore', 1)
            }
            return 'You win'
        } return 'You lose'
    }
    if (props.userChoice == 'paper') {
        if (props.computerChoice == 'rock') {
            updateLocalScore()
            if (localStorage.setScore) {
                localStorage.setScore = Number(localStorage.setScore) + 1
            } else {
                localStorage.setItem('setScore', 1)
            }
            return 'You win'
        } return 'You lose'
    }
    if (props.userChoice == 'scissors') {
        if (props.computerChoice == 'paper') {
            updateLocalScore()
            if (localStorage.setScore) {
                localStorage.setScore = Number(localStorage.setScore) + 1
            } else {
                localStorage.setItem('setScore', 1)
            }
            return 'You win'
        } return 'You lose'
    }

})

</script>
<template>
    <div class="userWrapper">
        <div class="resultInnerWrapper">
            <div class="userChoiceWrapper userChoiceAnimation">
                <p>You picked</p>
                <div class="outerUserChoice" :class="userChoiceClass">
                    <div class="innerUserChoice">
                        <img :src="userChoiceImage">

                    </div>
                </div>
            </div>

            <div v-if="data.showResult" class="userChoiceWrapper resultWrapper">
                <p>{{ result }} </p>
                <button @click="tryAgain()">Play again</button>
            </div>

            <div class="userChoiceWrapper computerChoiceAnimation">
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

