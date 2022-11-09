<template>
  <div id="app">
    <h1>Which would you choose?</h1>

    <WouldYouRather
        v-for="wyrQuestion in questions"
        v-bind:key="wyrQuestion.id"
        v-bind:question="wyrQuestion.question"
        v-bind:answer1="wyrQuestion.answer1"
        v-bind:answer2="wyrQuestion.answer2"
        v-bind:id="wyrQuestion.id"
        v-on:answer-changed="answerChanged">
    </WouldYouRather>
    <!-- when answer-changed event is received from child component, call the method answerChanged-->
    <!-- adds WouldYouRather component -->
    <!-- v-bind from parent data to child props -->
    <!-- v-bind: [prop in wyr.vue] = ["name in App.vue"]-->

    <ul>
      <li id="list-title">You would rather...</li>
     <!-- <li>{{ userSelectionMessage }}</li> not using this-->
      <li v-bind:key="choice" v-for="choice in choices">{{ choice }}</li>
    </ul>
  </div>
</template>

<script>
// console.log("app script reached")
import WouldYouRather from './components/WouldYouRatherQuestion.vue'
export default {
  name: 'App',
  components: { WouldYouRather },
  data() {
    return {
      questions: [
        {id: 0,
        question: 'be able to see things that are very far away, like binoculars, or be able to see things very close up, like a microscope?',
        answer1: 'have binocular eyes!',
        answer2: 'have microscope eyes!' },
        // userSelectionMessage:'You would rather ', // was testing different structure
        // choice:''}
        {id: 1,
         question: 'be completely invisible for one day or be able to fly for one day?',
         answer1: 'be invisible for one day!',
         answer2: 'be able to fly for one day!'},
        {id: 2,
          question: 'hang out for an hour with 10 puppies or 10 kittens?',
          answer1: 'HANG OUT WITH PUPPIES!!!',
          answer2: 'HANG OUT WITH KITTENS!!!'}
      ],
      choices: [],
      userSelectionMessage:''
    }
  }, // end data
      //https://conversationstartersworld/would-you-rather-questions/would-you-rather-questions-for-kids #21

  methods: {
    answerChanged(choice, id) {
      // console.log("answerChanged method reached")
      // console.log(choice, id)
      id ++
      // increase id count to count from 1 to 3 instead of 0 to 2
      //this.userSelectionMessage = `Thanks!  You chose ${choice} for question ${id}.`
      this.choices[id] = choice // test this to see what happens, from class, doesn't work
      // console.log(this.choices)
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
#list-title {
  font-family:'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
  color:black;
  font-size: larger;
  font-weight: bold;
}
li {
  color:purple;
  font-size: large;
  font-weight: bold;
  background-color: cornsilk;
}
</style>
