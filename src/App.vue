<template>
  <v-app top-navbar>
    <header>
      <v-toolbar>
        <v-toolbar-logo>IronMan HUD</v-toolbar-logo>
        <v-toolbar-items>
          <v-toolbar-item v-for='item in toolbarItems'>
            <router-link>{{ item.text }}</p>
          </v-toolbar-item>

        </v-toolbar-items>
      </v-toolbar>
    </header>
    <main>
      <v-content>
        <v-container fluid>
          <div id="getting-started">
            <v-card class="secondary">
              <v-card-text class="text-xs-center">
                <img src="public/v.png">
              </v-card-text>
            </v-card>
            <h2 class="primary--text">{{ question.question }}</h2>
            <div class="intro">
              <v-list>

                <v-list-item v-for='answer in question.answers'>
                  <v-list-tile target="_blank">
                    <v-button @click="select(answer)">{{answer}}</button>
                  </v-list-tile>
                </v-list-item>

              </v-list>
            </div>
          </div>
        </v-container>
      </v-content>
    </main>
  </v-app>
</template>

<script>
  const questions = [
    {question: 'Do you remember your dream?', answers: ['Yes', 'No', 'Kinda']},
    {question: 'Is today going to be a good day?', answers: ['Yes', 'No', 'I don\'t know']},
    {question: 'Which one of these people do you most want to spend time with today?', answers: ['Tariq', 'Packy', 'Jiro', 'Lily', 'Julian']}
  ]

  var index = 0

  export default {
    data () {
      return {
        item: {
          text: 'Get Started'
        },
        toolbarItems: [{text: 'Add Questions'}, {text: 'View Data'}],
        question: questions[index = 0]
      }
    },
    methods: {
      select (answer) {
        //talk to server
        this.question = questions[++index]
      }
    }
  }
</script>

<style lang="stylus">
  @import '../node_modules/vuetify/src/stylus/main'
  @import './css/main.css'
</style>
