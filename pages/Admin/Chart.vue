<template>
  <div class="card analytics-chart">
    <canvas ref="activity"></canvas>
  </div>
</template>

<script>
  import Chart from 'chart.js'
  export default {
    name: "Chart",
    mounted() {
      if (process.client) {
        const canvas = this.$refs.activity
        const ctx = canvas.getContext('2d')
        new Chart(ctx, {
          type: 'line',
          data: {
            labels: ['6 JUN', '7 JUN', '8 JUN', '9 JUN', '10 JUN', '11 JUN', '12 JUN', '13 JUN'],
            datasets: [
              {
                borderColor: '#7ED321',
                backgroundColor: '#7ED321',
                data: [7500, 7000, 5500, 6800, 5600, 6200, 7500, 7300],
                fill: false
              },
              {
                borderColor: '#4A90E2',
                backgroundColor: '#4A90E2',
                data: [6100, 5750, 2000, 4000, 3800, 5500, 6500, 4950],
                fill: false
              },
              {
                borderColor: '#D0021B',
                backgroundColor: '#D0021B',
                data: [1000, 1000, 2550, 3000, 2300, 500, 900, 2000],
                fill: false
              }
            ]
          },
          options: {
            legend: {
              display: false
            },
            elements: {
              line: {
                tension: 0 // disables bezier curves
              }
            },
            scales: {
              yAxes: [
                {
                  ticks: {
                    max: 8000,
                    min: 0,
                    stepSize: 2000
                  }
                }
              ]
            }
          }
        })
      }
    }
  }
</script>

<style scoped>

</style>
