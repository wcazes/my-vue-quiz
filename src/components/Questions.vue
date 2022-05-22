<template>
  <div class="q-container">
      <div class="progress">
          <div class="bar" :style="{ width: `${(answered / questions.length) * 100}%`}"></div>
          <div class="status">{{answered}} of {{questions.length}}</div>
      </div>
      <div class="single-question fade-in fad-out" v-for="(question, id) in questions" :key="id" v-show="answered === id">
        <h1 class="question">{{question.q}}</h1>
        <div class="answers">
        <div 
            class="answer"
            v-for="answer in question.answers"
            :key="answer.text"
            @click.prevent="selectAnswer(answer.is_correct)"
          > <p>{{ answer.text }}</p></div>
      </div>
        </div>
  </div>
</template>

<script>
export default {
    props:["questions", "answered"],
    emit:["question-answered"],
    methods:{
        selectAnswer(is_correct){
            this.$emit('question-answered', is_correct)
        }
    }
}
</script>

<style>
.progress{
    position: relative;
    width:50px;
    width:100%;
    background: rgb(194, 162, 162);
}
.status{
    position:absolute;
    top:15px;
    height:50px;
    width:100%;
    text-align: center;
    color:#efefef;
    font-weight: 900;
}
.bar{
    height:50px;
    background: #ff9494;
    transition: all 0.3s linear;
}

.question, .answer{
    padding:15px;
}
.question{
    background:#666;
    color:#efefef;
    font-weight: 400;
}
.answer{
    letter-spacing: 2px;
    font-weight: 900;
    margin:5px 0px;
    background:#efefef;
    border-radius: 5px;
    border-bottom:3px solid #dfdfdf;
}
.answer:hover{
    cursor: pointer;
    color:hsl(0, 0%, 94%);
    background:#9494FF;
}
.answer:last-child{
    border-bottom: 0px;
}


</style>