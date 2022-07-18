<template>

  <div>
  <p>Player "0" x "0" Computer</p>
  <hr>
 
  <template v-if="this.question">
  
  <h1 
    v-html="this.question" 
    v-bind:key="question"
  > </h1>

    <template v-for="(answer, index) in this.answers" v-bind:key="index">
      <input 
      :disabled="this.answerSubmitted"
        type="radio" 
        name="options" 
        :value="answer"
        v-model="chosenAnswer"
      >
      <label v-html="answer"></label><br>
    </template>
    <button v-if="!answerSubmitted" @click="this.submitAnswer" class="send" type="button">Send</button>

    <section v-if="answerSubmitted" class="result">
      <h4 
        v-if="this.chosenAnswer == this.correctAnswer"
        v-html="'&#9989; Congratulation, the answer: ' + this.correctAnswer + ' is correct.'">
        
      </h4>
      <h4 
        v-else
        v-html="'&#10060; I am sorry, you picked the wrong answer. The correct is: ' + this.correctAnswer + '.'">
          
      </h4>

      <button @click="this.getNewQuestion()" class="send" type="button">Next question</button>

    </section>
  </template>
    </div>
</template>

<script>

export default {
  name: 'App',

  data() {
    return {
      question: undefined,
      incorrectAnswers: undefined,
      correctAnswer: undefined,
      chosenAnswer: undefined,
      answerSubmitted: false
    }
  },
  computed: {
    answers() {
      var answers = JSON.parse(JSON.stringify(this.incorrectAnswers));
      answers.splice(Math.round(Math.random() * answers.length), 0,  this.correctAnswer);
      return answers;
    }
  },

  methods: {
    submitAnswer() {
      if (!this.chosenAnswer) {
        alert("Pick one of the options");
      } else {
        this.answerSubmitted = true
        if (this.chosenAnswer == this.correctAnswer){
          console.log("You got it right!");
        } else {
          console.log("You got it wrong!") 
        }
      }
    },

    getNewQuestion() {
      this.answerSubmitted = false;
      this.chosenAnswer = undefined;
      this.question = undefined;

      this.axios
      .get('https://opentdb.com/api.php?amount=1&category=18')
      .then((response) => {
        this.question = response.data.results[0].question;
        this.incorrectAnswers = response.data.results[0].incorrect_answers;
        this.correctAnswer = response.data.results[0].correct_answer;
      })
    }

  },

  created() {
    this.getNewQuestion();

  }
}
// https://opentdb.com/api.php?amount=1&category=18
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto;
  max-width: 960px;

  input[type=radio] {
    margin:12px 4px;
  }
  // button.send { -> THIS WAS ORIGINAL
  button {
    margin-top: 12px;
    height: 40px;
    max-width: 120px;
    padding: 0 16px;
    color: #fff;
    background-color: #1967c0;
    border: 1px solid #1967c0;
    cursor: pointer;
  }
}
</style>
