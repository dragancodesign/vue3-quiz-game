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
        type="radio" 
        name="options" 
        :value="answer"
        v-model="chosen_answer"
      >
      <label v-html="answer"></label><br>
    </template>
    <button @click="this.submitAnswer" class="send" type="button">Send</button>
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
      chosen_answer: undefined
    }
  },
  computed: {
    answers() {
      var answers = this.incorrectAnswers;
      answers.push(this.correctAnswer);
      return answers;
    }
  },

  methods: {
    submitAnswer() {
      if (!this.chosen_answer) {
        alert("Pick one of the options");
      } else {
        if (this.chosen_answer == this.correctAnswer){
          alert("You got it right!");
        } else {
          alert("You got it wrong!") 
        }
      }
    }
  },

  created() {
    this.axios
    .get('https://opentdb.com/api.php?amount=1&category=18')
    .then((response) => {
      this.question = response.data.results[0].question;
      this.incorrectAnswers = response.data.results[0].incorrect_answers;
      this.correctAnswer = response.data.results[0].correct_answer;
    })
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
