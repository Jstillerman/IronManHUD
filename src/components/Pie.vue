<script>
import { Doughnut } from 'vue-chartjs'

export default Doughnut.extend({
  props: [data],
  mounted () {
    // Overwriting base render method with actual data.
    this.renderChart({
      labels: this.data.answers.map(answer => answer.answer),
      datasets: [
        {
          label: 'GitHub Commits',
          backgroundColor: '#f87979',
          data: this.data.answers.map(answer => answer.count)
        }
      ]
    })
  }
})
</script>
