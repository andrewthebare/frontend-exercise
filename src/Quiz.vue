<template>
  <div>
    <!-- Feeds Question with each question value sequentially -->
    <div :key="question" v-if="this.questions[questionNum]">
      <Question @answer-question="onAnswer" :question='this.questions[questionNum]'/>
    </div>

    <div class="summary leftAlign" v-if="questionNum >= this.questions.length">
      <h2>Summary</h2>
      <div class="container" :key="i" v-for="i in this.answers">
        <div style="flex: 2; text-align: right;">
          <b>{{i.question}}</b>
        </div>
        <div style="flex: 1; text-align: left; padding-left: 12px;">
         <i>{{i.answer}}</i>
        </div>
      </div>
    </div>

  </div>

  
</template>

<script>
import Question from './Question.vue'

export default {
  props: {
    questions: {
      type: Array,
      required: true
    }
  },
  components:{
    Question,
  },
  methods:{

    /**
     * recieves the answer, stores it, and performs the logic 
     * to move the quiz along
     */
    onAnswer(answer){
      this.answers[this.questions[this.questionNum].text] = {
          question: this.questions[this.questionNum].text,
          answer: answer,
        };
      this.questionNum++;
    }
  },
  data() {
    return{
      answers:{},
      questionNum: 0,
    }
  }
};
</script>

<style>
.summary{
  display: block;
  max-width: 600px;
  margin: auto;

  text-align: center;


  background-color: #fcfcfc;
  border-radius: 15px;

  box-shadow: 10px 12px 132px 12px rgba(174,174,174,0.63);
-webkit-box-shadow: 10px 12px 132px 12px rgba(174,174,174,0.63);
-moz-box-shadow: 10px 12px 132px 12px rgba(174,174,174,0.63);
}

.summary > .container{
  display: flex;
  flex-direction: row;
  justify-content: center;

}
</style>
