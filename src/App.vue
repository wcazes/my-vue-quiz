<template>
  <div class="container">
    <Questions 
      v-if="answered < questions.length" 
      :questions="questions"
      :answered="answered"
      @question-answered="questionAnswered"

      />
    <Result v-else :total="totalCorrect" :results="results"/>

    <!-- <h1>Answered {{ answered }} | Correct {{totalCorrect}}</h1> -->
    <div class="buttons">
      <button v-if="answered === questions.length" @click.prevent="again">Play Again</button>
      <button v-if="quizOver === false && answered !== 5" @click.prevent="give">Give Up</button>
    </div>
  </div>
</template>

<script>
  import Questions from './components/Questions.vue'
  import Result from './components/Result.vue'

  export default{
    components:{Questions, Result},
    data(){
      return{
        answered: 0,
        totalCorrect: 0,
        quizOver: false,
        questions: [
          {
            q: "What is my name?",
            answers:[
              {
                text: "William",
                is_correct: true
              }, 
              {
                text: "Steve",
                is_correct: false
              }, 
              {
                text: "John",
                is_correct: false
              }, 
              {
                text: "Tim",
                is_correct: false
              }, 
              
            ]
          },
          {
            q: "What is my favorite color?",
            answers:[
              {
                text: "Red",
                is_correct:false 
              },
              {
                text: "Blue",
                is_correct:false 
              },
              {
                text: "Black",
                is_correct:true 
              },
              {
                text: "Pink",
                is_correct:false 
              },
            ]
          },
          {
            q: "What state am I from?",
            answers:[
              {
                text: "Texas",
                is_correct:false 
              },
              {
                text: "Ohio",
                is_correct:false 
              },
              {
                text: "Alabama",
                is_correct:false 
              },
              {
                text: "Louisiana",
                is_correct:true 
              },
            ]
          },
          {
            q: "At what age did I learn to code?",
            answers:[
              {
                text: "12",
                is_correct:false 
              },
              {
                text: "14",
                is_correct:true 
              },
              {
                text: "16",
                is_correct:false 
              },
              {
                text: "13",
                is_correct:false 
              },
            ]
          },
          {
            q: "What is my shoe size?",
            answers:[
              {
                text: "10",
                is_correct:false 
              },
              {
                text: "11",
                is_correct:false 
              },
              {
                text: "10.5",
                is_correct:true 
              },
              {
                text: "11.5",
                is_correct:false 
              },
            ]
          },          
        ],
        results:[
          {
            correct: 0, 
            text: "You didn't even get my name right.."
          },
          {
            correct: 1, 
            text:  "Not sure how you even found me.."
          },
          { 
            correct: 2, 
            text:  "You're going to have to do better than that.."
          },
          { 
            correct: 3, 
            text:  "You got lucky.."
          },
          {
            correct: 4, 
            text:  "Okay, you did alright.."
          },
          { 
            correct: 5, 
            text:  "I think you are obsessed with me.." 
          },
        ]
      }
    },

    methods: {
      questionAnswered(is_correct){
        if(is_correct){
          this.totalCorrect++;
        }
        this.answered++
      },
      give(){
        this.answered = 5,
        this.quizOver = ! this.quizOver
      },
      again(){
        this.totalCorrect = 0
        this.answered = 0
        this.quizOver = false
      }
    }
  }
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;900&display=swap');
/* #00FF00 */
/* ff9494 */
*{
  margin:0px;
  padding:0px;
  box-sizing: border-box;
}
body{
  background:#dfdfdf;
  color:#666;
  font-family: 'Roboto', sans-serif;
  font-size:18px;
}
.container{
  margin:50px auto;
  padding:10px;
  /* background:#efefef; */
  width:100%;
  max-width: 500px;
}
h1{
  font-size:1.5em;
}
.buttons{
  padding:15px;
  text-align: center;
  background:#efefef;
}
button{
  letter-spacing: 1px;
  text-transform: uppercase;
  padding:10px;
  font-weight:400;
  border-radius: 3px;
  border:0px;
  background: rgb(194, 162, 162);
}
button:hover{

  color:#efefef;
  background: #9494FF;
}

/* animations */
.fade-in {
  animation: fadeIn 1s;
  -webkit-animation: fadeIn 1s;
  -moz-animation: fadeIn 1s;
  -o-animation: fadeIn 1s;
  -ms-animation: fadeIn 1s;
  transition: all 0.3s linear;
}
@keyframes fadeIn {
  0% {opacity:0;}
  100% {opacity:1;}
}

@-moz-keyframes fadeIn {
  0% {opacity:0;}
  100% {opacity:1;}
}

@-webkit-keyframes fadeIn {
  0% {opacity:0;}
  100% {opacity:1;}
}

@-o-keyframes fadeIn {
  0% {opacity:0;}
  100% {opacity:1;}
}

@-ms-keyframes fadeIn {
  0% {opacity:0;}
  100% {opacity:1;}
}




</style>
