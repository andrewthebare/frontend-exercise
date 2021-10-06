<template>
  <div>
    <!-- Feeds Question with each question value sequentially -->
    <div :key="question" v-if="this.questions[this.questionNum]">
      <Question @answer-question="onAnswer" :question='this.questions[questionNum]'/>
    </div>

    <div class="summary leftAlign" v-if="questionNum >= this.questions.length">
      <h2>Summary</h2>
      <div class="container" v-for="(a, index) in this.answers" :key="a">
        <div style="flex: 2; text-align: right;">
          <b>{{questions[index].text}}</b>
        </div>
        <div style="flex: 1; text-align: left; padding-left: 12px;">
         <i>{{a}}</i>
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
      this.answers.push(answer)
    }
  },
  data() {
    return{
      answers:[],
    }
  },
  computed:{
    questionNum: function(){
      return this.answers.length;
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
