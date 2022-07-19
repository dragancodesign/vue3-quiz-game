## Vue3 Quiz Game using API 
<hr>

#### To install Vue CLI with Homebrew  

```brew install vue-cli```
### Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files: USED THIS COMMAND !!!
```
npm run lint

npm run dev
npm install vue-draggable-next

```
### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

## My commands to start project

Inside the Project folder run terminal command:  
```
vue create vue3-quiz-game
```
* Choose: Manually select features to see what Vue has to offer :  
1. Choose Vue version (as is (*),  
2. Babel (*) converts code to ES5,  
3.  TypeScript ( ) he is not going to use TS,  
4. Progressive Web App (PWA) Support ( ),  
5. Router ( ) to create multi-page app  
6. Vuex ( ) to KEEP centralized state for our app  
7. CSS Pre-processors (*) for using SASS, .scss ...  
8. Linter / Formatter (*) give us warning and throw errors if we are not doing things right, if we don't check this later will be harder to find what's going wrong?  
9. Unit Testing ( )  
10. E2E Testing ( )  
11. Press: ENTER  

NEXT STEPS:  
```
Now press Enter to choose the version of the Vue  
Vue CLI v5.0.8  
? Please pick a preset: Manually select features  
? Check the features needed for your project: Babel, CSS Pre-processors, Linter  
? Choose a version of Vue.js that you want to start the project with 3.x  
? Pick a CSS pre-processor (PostCSS, Autoprefixer and CSS Modules are supported by default): 
❯◉ Sass/SCSS (with dart-sass)  
? Pick a linter / formatter config: (Use arrow keys)  
❯◉ ESLint with error prevention only  
❯ ? Pick a linter / formatter config: Basic  
❯◉ Lint on save  
◉ ? Pick additional lint features: Lint on save  
? Where do you prefer placing config for Babel, ESLint, etc.?  
```
❯ ◉ Inside the package.json  
- dependencies are gonna be used on live server.  
- devDependencies are gonna be used only in our local project folder.  
- In public folder we will have the final files once we build our application.  
- during the development phase everything we gonna touch is inside the src folder.  
- main.js is the file where we will write some of the logic of our app but it is more for configuration, we will write logic inside each of the components.  
- COMPONENTS have .VUE extension, this the main one. It has all the logic and the style inside.  
```<template>``` tag we will put everything we want to show on the page (from here we can call some other component), it is like the```<body>``` element in .html file.  
```<script>``` has all the logic we have on the page: data properties, the methods, the life cycle hooks,  
```<style>``` has all the styles of the component it is in.   
This is Vue.js basic structure component  

### Starting the local server : 
With this approach we are not gonna use Live Server from VS Code but we gonna serve the application using npm, using: npm run serve That's it!  
App running at:  
- Local:   http://localhost:8080/  
- Network: http://192.168.1.181:8080/  

Section 3. Quiz Game Project using the Vue CLI  
Video: 23. Clean up Unused Component and HTML Structure  

Using: https://opentdb.com/api_config.php to get questions !  
Choose 1 Question (at the time) Select: Any Category, Select difficulty: Any Difficulty. Generate API, copy API link and open in new tab to see if it works.  
We get JSON and he has the Chrome extension: JSON View  

He deleted the message from the App.vue component and it throws the error.  
The ```<template>``` requires a child element !  

Section 3. Quiz Game Project using the Vue CLI  
Video: 24. HTTP Requests with Axios  

Search: HTTP Requests in Vue js -> Use: AXIOS  

Search: axios vue 3  
### FROM THIS WEBSITE USE THE INSTRUCTIONS:  
https://www.npmjs.com/package/vue-axios  

To install axios just run this command:  
```
npm i vue-axios  // I HAVE USED THIS COMMAND TO INSTALL AXIOS 
```
ES6 Module: or the command down:  
```
    npm install --save axios vue-axios
```
All installations we have to do from external libraries we have to do inside the project folder!
Import libraries in entry file:
Paste this in the main.js file  
```
import * as Vue from 'vue' // in Vue 3
import axios from 'axios'
import VueAxios from 'vue-axios'
```
Usage in Vue 3:
```
const app = Vue.createApp(...)
app.use(VueAxios, axios)
```
Script:  
Just add 3 scripts in order: 
```
vue, 
axios, and 
vue-axios
``` 
to your document.  
IF WE WANT TO INSTALL package WITHOUT KILLING THE PROCESS IN one terminal window, we can open another terminal window and run the installation!  
WHEN INSTALLING PACKAGES BETTER USE BIG TERMINAL WINDOW TO SEE  BETTER ANY ERROR MESSAGES ! ! !
#### To check errors in packages database for: npm, python, ...  
https://openbase.com/js/npm/versions  

He adds in main.js  
```.use(VueAxios, axios)```  after the createApp in the same line, so it looks:  
```createApp(App).mount('#app').use(VueAxios, axios)```  
We also can break lines inside main.js file :  
```
createApp(App)
.mount('#app')
.use(VueAxios, axios)
```
and this looks more readable.  

ERROR appeared to him, so he run:  
```npm install --save axios vue-axios```
and he adds: .use(VueAxios, axios) in main.js after  
He adds in main.js  
```.use(VueAxios, axios)```  
after the createApp in the same line, so it looks:   
```createApp(App).mount('#app').use(VueAxios, axios)```  
Now this shows in package.json file that axios is in our "dependencies" list.  

#### When we are installing dependencies we always look in the package.json file !  
**In this project we delete now the HelloWorld.vue FILE as we don't need it any more !**  

* In App.vue I have changed the button name for style  "button.send" to just "button" before the curly brackets !  
### Now is the Time to learn how to make HTTP Requests with Axios - Section 3 - Video 25: Making requests to the Open Trivia API  
From the site:  
https://www.npmjs.com/package/vue-axios  
he uses:  
```
this.axios.get(api).then((response) => {
  console.log(response.data)
})
```
because we are inside the main component this will work the best!  
We want to do this right after we create the application. So we have a created life cycle hook.  
And at this point, we are going to have the data properties created.  
So this is the exact point that we want to do this, because then we are going to get the things that the API provides to us and we are going to send these values to our data properties.  

So right after we have the name in the previous examples, we didn't have the name.  
This is because now we are working with components.  
So this is the the name of the components that we are inside.  
So right here we can start putting the data properties, the methods and also the lifecycle hooks, so the one we are going to use is the created.  

### 25. Making requests to the Open Trivia API 
Now inside App.vue  
We have :  
```
export default {
  name: 'App',

  created() {
    this.axios
    //.get(api) -> WHERE WE HAD API NOW WE PUT link inside the '': 
    .get('https://opentdb.com/api.php?amount=1&category=18')
    .then((response) => {
      console.log(response.data)
    })
  }
}
```
### Error here with axios (SOLVED): 
Inside the main.js; FIRST we had listed:
```
createApp(App)
.mount('#app')
.use(VueAxios, axios)
```
*THE SOLUTION: is: (ALWAYS READ THE FIRST LINE OF ERROR, IT CAN CAUSE ALL THE OTHER ERRORS THAT ARE DOWN THERE !!!)* 
1. First: ```createApp(App)``` on the top
2. Second: All components here is: 'axios' 
3. Third: AT THE END MOUNT the APP ```.mount('#app')``` :
```
createApp(App)
.use(VueAxios, axios)
.mount('#app')
```
- Adding 

```
export default {
  name: 'App',

  created() {
    this.axios
    .get('https://opentdb.com/api.php?amount=1&category=18')
    .then((response) => {
      /* console.log(response.data) (-> OLD CODE) */
      console.log(response.data.results) (-> NEW corrected CODE !!!)
    })
  }
}
```
### 26. Showing the Question Data on the Page ( DECLARATIVE RENDERING )
Before creating a hook let's create the property for our data.  
So let's go to visuals to decode and before the created hook, let's, as usual, just create the property for our data.  
Let's remember that this is a function. So we do like this just like we've been doing before.  
This function needs to return something which is going to be the object with our data properties.  
All we need from this object is:  
- the correct answer,  
- the incorrect answers and  
- the question.  
So let's create data properties for these.  
So let's create the first one called  
- Question, which we can start this as undefined for now and now.  
- Incorrect and  
- Answers.  
Which is going to be an array, if you want, you can leave an empty array or you can just use undefined !
#### THIS WORKS FINE: 
```
export default {
  name: 'App',

  data() {
    return {
      question: undefined,
      incorrectAnswers: undefined,
      correctAnswer: undefined
    }
  },

  created() {
    this.axios
    .get('https://opentdb.com/api.php?amount=1&category=18')
    .then((response) => {
      this.question = response.data.results[0].question;
      this.incorrectAnswers = response.data.results[0].incorrect_answers;
      this.correctAnswer = response.data.results[0].correct_answer;
      // console.log(response.data.results[0])
    })
  }
}
```
#### EXPLANATION WHY WE USE 'this' KEYWORD !!! 
*This is because we are now working with components.*
*We are working with this dot .vue files.*
*And here TO BE ABLE TO ACCESS its data properties, we need to use that 'this' key word.*  
So inside the App.vue in the 'template' we code the question like this:  
## ERROR TO SOLVE : -> SOLVED = I HAVE REMOVED THE CONTENT FROM BETWEEN THE ```<h1>``` and ```</h1>``` so it's empty now and that's it == WORKS !
```
<h1> --> Works but creates problem with 
<!-- CREATES THE ERROR -->
<h1>{{ this.question }}</h1> -> WORKS BUT NOT WHAT I EXACTLY NEED !!!
<h1 v-html="this.question">{{ this.question }}</h1> -> DOES NOT WORK BUT IS WHAT I EXACTLY NEED = SHOWS ERRORS AND BRAKES SITE !!!  
<h1 v-html="this.question">{{ el.outerHTML }}</h1>  -> DOES NOT WORK

<h1 v-html="('this.question;')"> -> DOES NOT WORK -> FROM GitHub vuejs/core repo (https://github.com/vuejs/core/issues/5439)
<h1 v-html="'this.question';"> -> DOES NOT WORK
<h1 v-html="('this.question')"> -> DOES NOT WORK
```
### Now the CORRECT HTML looks like this: 
##### Nothing in between ```<h1>``` AND ```</h1>```
```
<h1 
  v-html="this.question" 
  v-bind:key="question"
></h1>
```
#### *But because we want to display as a text any html entity*

When the DATA is coming with API we have sometimes some HTML with the sentences, and HTML will not pass the html but the code as it is.  
So to display on page something that has an html element we have to use Vue HTML DIRECTIVE  
 We are telling to Vue that what we are passing here is HTML. 

This line has changed and works:  
```this.incorrectAnswers = response.data.results[0].incorrect_answers;```  

####  Commit 02: Added answers.splice(Math.round + Math.random + answers.length) in App.vue file
 
```
computed: {
  answers() {
    // var answers = this.incorrectAnswers;
    var answers = JSON.parse( JSON.stringify(this.incorrectAnswers) );
    // answers.push(this.correctAnswer);
    // answers.splice(0, 0, this.correctAnswer);
    answers.splice(Math.round(Math.random() * answers.length), 0, this.correctAnswer);
    // answers.push("test");
    return answers;
  }
},
```  
Difference between Computed Properties and Methods:  
- Search in Vue.js documentation:  
https://vuejs.org/guide/essentials/computed.html  

## GitHub: Deleting the last commit: This command WORKED:  
*Be careful ! ```reset --hard``` will remove your local (uncommitted) modifications, too.*  

#### 1st STEP:
```git reset --hard HEAD~2```  in this case did satisfied the task to delete the latest commit and go back to the previous one !!!  
 
#### 2nd STEP:  
```git push --force origin main``` →  WORKED: Deleted the commit from the list of commits on GitHub repository !  
- Now I see the typo 'Commmit 01' instead of "Commit 01", but now never mind !  

### Now everything works correctly at: Video 30. Submitting the answer  
**The HTML part**
```
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
```
**The script part:**
```
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

</script>
```
### Presenting the Result  
(Video 31)  
Inside the methods:  
```
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
    }
  },
  ```
## App.vue file now at the point before making the Next Question Dynamic:  
**1. The HTML part inside the template tag looks like this:**  
```html
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
        v-if="this.chosenAnswer == this.correctAnswer">
        &#9989; Congratulation, the answer: "{{this.correctAnswer}}" is correct.
      </h4>
      <h4 
        v-else>
          &#10060; I am sorry, you picked the wrong answer. The correct is: "{{this.correctAnswer}}".
      </h4>

      <button v-if="answerSubmitted" class="send" type="button">Next question</button>

    </section>
  </template>
    </div>
</template>
```
**2. The complete script tag until now looks like this:**  
```js 
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
```
**3. The style tag remains the same:**  
```css
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
```
## Created and imported component ScoreBoard.vue
Video No. 33 → DONE ! ! !  

COMPONENT CONTENT:  
```html
<template>

<section class="score">
Player <span>0</span> x <span>0</span> Computer.
</section>

</template>

<script>
   export default {

   }

</script>

<style lang="css">
    section.score {
        border-bottom: 1px solid black;
        padding: 24px;
        font-size: 18px;
}
    span {
        padding: 8px;
        font-weight: bold;
        border: 1px solid blue;
    }

</style>
```

### Final settings: 

**props** - They are two ways to use props.  
https://vuejs.org/guide/components/props.html#prop-passing-details  
1. We can pass an array of strings 
```html
<!-- Even though the array is static, we need v-bind to tell Vue that -->
<!-- this is a JavaScript expression rather than a string.            -->
<BlogPost :comment-ids="[234, 266, 273]" />

<!-- Dynamically assign to the value of a variable. -->
<BlogPost :comment-ids="post.commentIds" />
```
2. We can use an object and assign a type of this prop. This can be useful if you want to receive warnings if the type is not correct ! Example: we have loseCount property and we set it as a number and then we receive a string instead. We can have that kind of warning.  
```html
<!-- Even though the object is static, we need v-bind to tell Vue that -->
<!-- this is a JavaScript expression rather than a string.             -->
<BlogPost
  :author="{
    name: 'Veronica',
    company: 'Veridian Dynamics'
  }"
 />

<!-- Dynamically assign to the value of a variable. -->
<BlogPost :author="post.author" />
```
### Here in my project:  
Data here is passed, but if we want this to be dynamic we have to pass at the beginning of each element inside the line in App.vue :  
```html
<!-- In App.vue -->

    <ScoreBoard :winCount="this.winCount" :loseCount="this.loseCount" />

And in the ScoreBoard.vue: for data to appear

<!-- In ScoreBoard.vue -->
<template>
     
    <section class="score">
    Player <span>{{this.winCount}}</span> x <span>{{this.loseCount}}</span> Computer.
    </section>
     
    </template>
```
## The final words:  
**The project is practically done.**  
*The things that can be improved are:*  
- The score is kept as long as we are pressing 'Next question button'. If we refresh the page then the results are lost.  
- To improve this we can store data in the LOCAL STORAGE to keep it.  
- For the beginning of using Vue.js I am really satisfied !  
- Now on my way to next project 🎯 😊 🙏  
