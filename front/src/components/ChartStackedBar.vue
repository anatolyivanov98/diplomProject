<div class="col l12">
  <div class="table-chart">
    <canvas id="canvas"></canvas>
  </div>
</div>

<script>
  import {Bar} from 'vue-chartjs';
  export default {
    name: "ChartStackedBar",
    data: () =>({
      chartData: ''
    }),
    extends: Bar,
    mounted() {
      this.chartData = this.$store.state.table.chartData

      let counter = 0
      for( let n in this.chartData.header) {
        counter++
      }
       const Colors = [
        '#ffeda0',
        '#fed976',
        '#feb24c',
        '#fd8d3c',
        '#fc4e2a',
        '#e31a1c',
        '#bd0026',
        '#800026'
      ]

      let dd = []
      for( let i = 0; i < counter; i++){
            dd[i] =  {label: this.chartData.header[i], data: this.chartData.data[i], backgroundColor:Colors[i] }
      }

      const chartOptions = {
          scales: {
            xAxes: [{
              stacked: true
            }],
            yAxes: [{
            stacked: true
            }]
          }
        }

      const allData = {
          labels: this.chartData.labels,
          datasets: dd
        }

      this.renderChart(allData, chartOptions)
   }
}

</script>

<style scoped lang="scss">

</style>





