<template>
  <v-app id="example-1" top-toolbar footer>
  <v-toolbar>
    <v-toolbar-title>IronMan HUD</v-toolbar-title>
  </v-toolbar>
  <main>
    <v-content>
      <questions @submitted='dataVisible = !dataVisible' v-if="!dataVisible"></questions>
      <dataviewer v-if="dataVisible"></data>
    </v-content>
  </main>
  <v-footer>Footer</v-footer>
</v-app>
</template>

<script>

  import Questions from './components/Questions.vue'
  import Data from './components/Data.vue'

  export default {
    data () {
      return {
        dataVisible: false
      }
    },
    components: {
      questions: Questions,
      dataviewer: Data
    }
  }
</script>

<style lang="stylus">
  @import '../node_modules/vuetify/src/stylus/main'
  @import './css/main.css'
</style>
