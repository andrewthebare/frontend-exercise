<template>
  <div class="question">
    <h2>{{question.text}}</h2>
    <div class="container">
      <div class = "leftAlign">
        <div :key="answer" v-for= "answer in question.answers">
          <input type="radio" :name="question.text" :value="answer">{{answer}}
        </div>
      </div>
      <button @click="onClick()">Advance</button>
    </div>
  </div>
</template>

<script>
export default {
  name:'Question',
  props:{
    question: Object,
  },

  methods:{
    onClick(){
      let answerSelected = document.querySelector('input[name="'+ this.question.text+ '"]:checked');
      if(!answerSelected){
        alert('Please Select an Answer');
      }else{
        //passes the answer up the path to Quiz
        this.$emit('answer-question', answerSelected.value)
      }
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