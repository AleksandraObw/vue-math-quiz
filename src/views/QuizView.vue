<script>
    export default {
        data() {
            return {
                firstNumber: Math.floor(Math.random()*11),
                secondNumber: Math.floor(Math.random()*11),
                symbolIndex: Math.floor(Math.random()*2),
                symbols: ['+', '-'],
                counter: 1,
                correctAnswers: 0,
                isGameOver: false,
                answer: '',
                isResultReady: false,
                salutation: 'Так себе результат...',
                lastResults: []
            }
        },

        methods: { 
            startTheGame() {
                this.renewExample();
                this.isGameOver = false;
                this.isResultReady = false;
                this.correctAnswers = 0;
                this.counter = 1;
                this.salutation = 'Так себе результат...';
            },

            checkAnswer() {
                    if (this.answer == '') {
                        this.answer == 0
                    }
                    if (this.symbolIndex == 0) {
                        if (this.firstNumber + this.secondNumber == this.answer) {
                            this.correctAnswers = this.correctAnswers + 1;
                        } else {}
                    } else {
                        if (this.firstNumber - this.secondNumber == this.answer) {
                            this.correctAnswers = this.correctAnswers + 1;
                        }
                    }
                    this.counter = this.counter + 1
                    if (this.counter > 10) {
                        this.isGameOver = true;
                    } else {
                        this.renewExample();
                    }
                
            },

            getResult() {
                this.isGameOver = false;
                this.isResultReady = true;
                if (this.correctAnswers == 10) {
                    this.salutation = 'Шикарно!'
                } else if (this.correctAnswers > 7) {
                    this.salutation = 'Отлично!'
                } else if (this.correctAnswers > 5) {
                    this.salutation = 'Хорошо!'
                }
                this.lastResults.push(this.correctAnswers)
            },

            renewExample() {
                this.firstNumber = Math.floor(Math.random()*11);
                this.secondNumber = Math.floor(Math.random()*11);
                if (this.secondNumber > this.firstNumber) {
                    this.symbolIndex = 0
                } else {
                    this.symbolIndex = Math.floor(Math.random()*2);
            }
            this.answer = ''
            }
        }
    }
</script>

<template>
  <div class="quiz-screen">

        <div class="quiz" v-if="isGameOver">
            <p class="text">Тест пройден</p>
            <button class="button" @click="getResult()">Узнать результат!</button>
        </div>

        <div class="quiz" v-else-if="isResultReady">
            <p class="text"> Ты правильно решил {{ correctAnswers }} из 10 примеров. {{ salutation }}</p>
            <button class="button" @click="startTheGame()">Пройти тест заново</button>
            <p class="text">Последние результаты: {{ lastResults }}</p>
        </div>

        <div class="quiz" v-else>
            <div class="quiz__counter">{{ counter }} <span> из 10</span></div>
            <div class="quiz__example">{{ firstNumber }} {{ symbols[symbolIndex] }} {{ secondNumber }}</div>
            <input class="quiz__input" v-model="answer" type="text" maxlength="3" autofocus onkeypress='return event.charCode >= 48 && event.charCode <= 57'>
            <button class="button" @click="checkAnswer()">Готово!</button>
        </div>

  </div>

  
</template>

<style scoped>
    .quiz-screen {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }
    .quiz {
        display: flex;
        flex-direction: column;
        justify-content: space-evenly;
        row-gap: 1em;
    }
    .quiz__counter {
        color: #44633F;
        font-weight: 800;
        text-align: right;
    }
    .quiz__example {
        color: #032704;
        font-size: 2.5em;
        font-weight: 800;
        text-align: center;
    }
    .button {
        padding: .5em .5em;
        background-color: #F7F7FF;
        border: 1px solid #EAEAEA;
        outline: 4px solid #EAEAEA;
        transition: all .5s ease-in-out;
        color: #032704;
        font-size: 1em;
        font-weight: 800;
        text-decoration: none;
    }
    .button:hover {
        outline-offset: 8px;
        cursor: pointer;
    }
    .quiz__input {
        padding: .5em .5em;
        background-color: #F7F7FF;
        border: 1px solid #EAEAEA;
        color: #032704;
        font-size: 1em;
        font-weight: 800;
    }
    .text {
        color: #032704;
        font-size: 1.5em;
        font-weight: 600;
        text-wrap: balance;
        text-align: center;
    }
</style>