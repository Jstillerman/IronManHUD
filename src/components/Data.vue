<template lang="html">
  <v-container>
    <pie v-for="question in questions" :data="question"><pie>
  </v-container>
</template>

<script>
import Pie from './Pie.vue'

export default {
  components: {
    Pie
  },
  data () {
    return {
      questions: [
        {
          question: "Is today going to be a good day?",
          answers: [
            {answer: 'Yes', count: 3},
            {answer: 'No', count:2}
          ]
        }
      ]
    }
  },
  methods: {
    select (answer) {
      //talk to server

    }
  }
}
</script>

<style lang="css">
</style>
