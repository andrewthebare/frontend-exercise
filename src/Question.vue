<template>
  <div class="question">
    <div style="display: block; width: 85%">
      <h2>{{question.text}}</h2>
      <div class="container">
        <div class = "leftAlign">
          <div :key="answer" v-for= "answer in question.answers">
            <input v-model="answerSelected" type="radio" :name="question.text" :value="answer">{{answer}}
          </div>
        </div>
        <button v-if="answerSelected!==null" @click="onClick()">Advance</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name:'Question',
  props:{
    question: Object,
  },
  
  data() {
    return{
      answerSelected: null,
    }
  },

  methods:{
    onClick(){
      //passes the answer up the path to Quiz
      this.$emit('answer-question', this.answerSelected)
      this.answerSelected = null;
    }
  }
}
</script>

<style>


body{
  background-color: #E3F8F8;
}

.leftAlign{
  text-align: left;
}

div .question{
  display: flex;
  max-width: 600px;
  min-height: 200px;
  margin: auto;

  text-align: center;
  justify-content: center;
  align-content: center;


  background-color: #fcfcfc;
  border-radius: 15px;

  box-shadow: 10px 12px 132px 12px rgba(174,174,174,0.63);
-webkit-box-shadow: 10px 12px 132px 12px rgba(174,174,174,0.63);
-moz-box-shadow: 10px 12px 132px 12px rgba(174,174,174,0.63);
}

button{
  all: unset;
  cursor: pointer;

  padding: 4px;
  margin: 3px;
  border: 1pt solid #121212;

  background-color: #D85427;
  color: #fcfcfc;
}
</style>