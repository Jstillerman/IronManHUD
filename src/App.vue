<template>
  <v-app id="example-1" top-toolbar footer>
  <v-toolbar>
    <v-toolbar-title>IronMan HUD</v-toolbar-title>
  </v-toolbar>
  <main>
    <v-content>
      <v-container>
        <h1 primary>Here are some questions</h1>
        <div v-for="question in questions">
          <v-card>
            <v-card-text>
              <div>{{ question.question }}</div>
            </v-card-text>
          </v-card>
          <v-card class="blue darken-1 white--text">
            <v-card-text>
              <v-btn v-for="answer in question.answers" primary dark ripple>{{ answer }}</v-btn>
            </v-card-text>
          </v-card>
          <br>
        </div>
      </v-container>
    </v-content>
  </main>
  <v-footer>Footer</v-footer>
</v-app>
</template>

<script>

  var index = 0

  export default {
    data () {
      return {
        item: {
          text: 'Get Started'
        },
        questions: [
          {question: 'Do you remember your dream?', answers: ['Yes', 'No', 'Kinda']},
          {question: 'Is today going to be a good day?', answers: ['Yes', 'No', 'I don\'t know']},
          {question: 'Which one of these people do you most want to spend time with today?', answers: ['Tariq', 'Packy', 'Jiro', 'Lily', 'Julian']}
        ],
        toolbarItems: [{text: 'Add Questions'}, {text: 'View Data'}]
      }
    },
    methods: {
      select (answer) {
        //talk to server

      }
    }
  }
</script>

<style lang="stylus">
  @import '../node_modules/vuetify/src/stylus/main'
  @import './css/main.css'
</style>
