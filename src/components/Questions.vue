<template lang="html">
  <v-container>
    <h1 primary>Here are some questions</h1>
    <div v-for="question in questions">
      <v-card class="blue darken-1 white--text">
        <v-card-text>
          <div>{{ question.question }}</div>
        </v-card-text>
      </v-card>
      <v-card>
        <v-card-text>
          <div>
            <v-radio :name="question.question" :id="'b'+Math.random()" v-for="answer in question.answers" :label="answer.text" v-model="answer.picked"></v-radio>
          </div>
        </v-card-text>
      </v-card>
      <br>
    </div>
    <button primary dark v-if="inputComplete" @click='submitData()'>Submit</v-btn>
  </v-container>
</template>

<script>
import Server from '../Server'

var server = new Server()

export default {
  data () {
    return {
      item: {
        text: 'Get Started'
      },
      questions: [
        {id: 0, question: 'Do you remember your dream?', answers: [{text:'Yes', picked: false}, {text:'No', picked: false}]},
        {id: 1, question: 'Is today going to be a good day?', answers: [{text:'Yes', picked: false}, {text:'No', picked: false}]},
        {id: 2, question: 'Which one of these people do you most want to spend time with today?', answers: [{text:'Yes', picked: false}, {text:'No', picked: false}]}
      ]
    }
  },
  computed: {
    inputComplete(){
      return this.questions.filter((q) => q.answers.filter(a => a.picked).length > 0).length == this.questions.length
    }
  },
  methods: {
    submitData () {
      server.dealWith(this.questions.map(q => {
        return q.answers.filter((a) => {return a.picked})[0].text
      }))
      this.$emit('submitted')
    }
  }
}
</script>

<style lang="css">
</style>
