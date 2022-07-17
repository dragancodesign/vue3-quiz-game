<template>

<p>Player "0" x "0" Computer</p>
<div>

<hr>
<!-- v-html error: "VueCompilerError: v-html will override element children."
at /Users/username/Dev_Vue/Vue3Quiz/project4-quiz-game-initial/src/App.vue:9:3 -->
<h1>
  {{this.question}}
</h1>

<input type="radio" name="options" value="True">
<label>True</label><br>

<input type="radio" name="options" value="True">
<label>False</label><br>

<button>Send</button>
</div>

</template>

<script>

export default {
  name: 'App',

  data() {
    return {
      question: undefined,
      incorrectAnswers: undefined,
      correctAnswer: undefined
    }
  },
  computed: {
    answers() {
      var answers = this.incorrectAnswers;
      answers.push(this.correctAnswer);
      return answers;
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
