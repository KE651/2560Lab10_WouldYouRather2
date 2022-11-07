<template>
  <div class="wyr">
    <h2>Please make your choice!</h2>
    <h3>{{ questionData.question }}</h3>

    <input class="button" type="radio" v-model="choice"
           v-bind:value="questionData.answer1" v-on:change="choiceMade">
    <label>{{ questionData.answer1 }}</label>

    <input class="button" type="radio" v-model="choice"
           v-bind:value="questionData.answer2" v-on:change="choiceMade">
    <label>{{ questionData.answer2 }}</label>
    <br><br>

  </div>
</template>

<script>
export default {
  name: 'WouldYouRather',
  props: {
    questionData: Object
    //props are for data given to child by parent, component should not modify props
  },
  data() {
    return {choice:''}
    //choice will update in devtools when radio buttons are selected
    //data function is for data that is used internally to the component
  },
  methods: {
    choiceMade() {
      //emit an event 'answer-changed' with value of selection
      this.$emit('answer-changed', this.choice, this.questionData.id)
      // name of event is 'answer-changed', convention is for dashes in events
      // $emit(name-of-event, argument1, argument2, ..)
    }
  } // end methods
} // end export
// props are for data provided by a parent component (App.vue in this case)
//devtools will show props for this file and data for App.vue

</script>

<style scoped>

.wyr {
  margin: 30px;
  border: 4px purple solid;
  color: black;
  background-color: azure;
  font-style:oblique
}
</style>