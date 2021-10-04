<template>
  <div class="question">
    <h2>{{question.text}}</h2>
    <div :key="answer" v-for= "answer in question.answers">
      <input type="radio" :name="question.text" :value="answer">{{answer}}
    </div>
    <button @click="onClick()">Advance</button>
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
      // console.log('clicked',  this.question.text)

      let answerSelected = document.querySelector('input[name="'+ this.question.text+ '"]:checked');
      if(!answerSelected){
        alert('Please Select an Answer');
      }else{
        //passes the answer up the path to Quiz
        this.$emit('answer-question', answerSelected.value)
      }



      // if(document.querySelector('input[name="{{this.question.text}}"]:checked').value){
      // }
    }
  }
}
</script>