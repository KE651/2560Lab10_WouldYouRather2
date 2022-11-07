<template>
  <div id="app">
    <h1>Would you rather...</h1>
    <would-you-rather
        v-for="wyrQuestion in questions"
        v-bind:key="wyrQuestion.id"
        v-bind:question="wyrQuestion.question"
        v-bind:answer1="wyrQuestion.answer1"
        v-bind:answer2="wyrQuestion.answer2"
        v-on:answer-changed="answerChanged">
      <!-- when answer-changed event is received from child component, call the method answerChanged-->
    </would-you-rather>
    <!-- adds WouldYouRather component -->
    <!-- v-bind from parent data to child props -->

    <ul>
      <li v-bind:key="choice" v-for="choice in choices">{{ choice }}</li>
    </ul>
  </div>
</template>
<!-- v-bind: [prop in wyr.vue] = ["name in App.vue"]-->

<script>
import WouldYouRather from './components/WouldYouRatherQuestion.vue'
export default {
  name: 'App',
  components: {WouldYouRather},
  data() {
    return {
      questions: [
        {id: 0,
        question: 'be able to see things that are very far away, like binoculars, or be able to see things very close up, like a microscope?',
        answer1: 'binocular eyes!',
        answer2: 'microscope eyes!'},
        {id: 1,
         question: 'be completely invisible for one day or be able to fly for one day?',
         answer1: 'invisible for one day!',
         answer2: 'able to fly for one day!'},
        {id: 2,
          question: 'hang out for an hour with 10 puppies or 10 kittens?',
          answer1: 'PUPPIES!!!',
          answer2: 'KITTENS!!!'}
      ],
      choices: []
      //https://conversationstartersworld/would-you-rather-questions/would-you-rather-questions-for-kids #21
    }
  }, // end data
  methods: {
    answerChanged(choice, id) {
      this.userSelectionMessage = `Thanks!  You chose ${choice} for question ${id}.`
      this.choices.push(choice) // test this to see what happens, from class, doesn't work
      // use id to update
    }
  } // end methods
}  // end export
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: darkgreen;
  margin-top: 60px;
  border-top:1px fuchsia solid;
}
</style>
