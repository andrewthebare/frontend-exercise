## Array Storage
   1. Refactored answers to be stored as an array in Quiz data
   2. Summary is now made with a for loop through the answer array with the index of the loop being used to fetch the question related to a particular answer
      1. The (i, index) syntax is pretty neat, never seen that before
## QuestionNum
   1. QuestionNum is now a computed prop based on the length of the answers array
## User Input
   1. v-model maps to the new varaible of answerSelected
      1. Very neat, My favorite part
## Error Message
   1. Button is only displayed if an answer is selected

Summary

I've never used Vue before, however, it's been a neat learning experience. I really appreciate the ability to write logical operations into the html portion of the component, it's similar to Shopify's liquid language
