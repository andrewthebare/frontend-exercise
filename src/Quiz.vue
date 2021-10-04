<template>
  <div>
    {{ JSON.stringify(questions, null, 2) }}
    <div :key="question" v-if="this.questions[questionNum]">
      <Question @answer-question="onAnswer" :question='this.questions[questionNum]'/>
    </div>

    <div v-if="questionNum >= this.questions.length">
      <h2>Review</h2>
      <div :key="i" v-for="i in this.answers">
        <b>{{i.question}}</b> <i>{{i.answer}}</i>
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
