<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App with Chart.js"/>
    <Chart class="Chart" :chartData="chartData" :options="options" />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import Chart from './components/Chart'

export default {
  name: 'App',
  data () {
    return {
      chartData: {
        labels: ['January', 'February', 'March', 'April', 'May'],
        datasets: [
          {
            label: 'Sample1',
            data: [28, 20, 30, 40, 50],
            backgroundColor: [
              'rgba(255, 99, 132, 0.2)',
              'rgba(54, 162, 235, 0.2)',
              'rgba(255, 206, 86, 0.2)',
              'rgba(75, 192, 192, 0.2)',
              'rgba(153, 102, 255, 0.2)',
              'rgba(255, 159, 64, 0.2)'
            ],
            borderColor: [
              'rgba(255, 99, 132, 1)',
              'rgba(54, 162, 235, 1)',
              'rgba(255, 206, 86, 1)',
              'rgba(75, 192, 192, 1)',
              'rgba(153, 102, 255, 1)',
              'rgba(255, 159, 64, 1)'
            ],
            borderWidth: 1
          }
        ]
      },
      options: {
        responsive: true,
        maintainAspectRatio: false,
        scales: {
          xAxes: [
            {
              scaleLabel: {
                display: true,
                labelString: 'Month'
              }
            }
          ],
          yAxes: [
            {
              ticks: {
                beginAtZero: true,
                stepSize: 10,
                callback: function (label) {
                  return label + ' 点';
                }
              }
            }
          ],
        },
        tooltips: {
          callbacks: {
            label: function (tooltipItem) {
              return tooltipItem.yLabel + ' 点';
            }
          }
        }
      }
    }
  },
  components: {
    HelloWorld,
    Chart
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.Chart {
  width: 600px;
  margin: 0 auto;
}
</style>
