<template>
  <section class="container">
    <h1>Demo examples of vue-chartjs</h1>
    <div class="columns">
      <div class="column">
        <h3>Line Chart</h3>
        <line-chart></line-chart>
      </div>
      <div class="column">
        <h3>Bar Chart</h3>
        <bar-chart></bar-chart>
      </div>
    </div>
    <div class="columns">
      <div class="column">
        <h3>Bubble Chart</h3>
        <bubble-chart></bubble-chart>
      </div>
      <div class="column">
        <h3>Reactivity - Live update upon change in datasets</h3>
        <reactive :chart-data="datacollection"></reactive>
        <button class="button is-primary" @click="fillData()">Randomize</button>
      </div>
    </div>
  </section>
</template>

<script>
  import LineChart from '@/components/LineChart'
  import BarChart from '@/components/BarChart'
  import BubbleChart from '@/components/BubbleChart'
  import Reactive from '@/components/Reactive'

  export default {
    name: 'VueChartJS',
    components: {
      LineChart,
      BarChart,
      BubbleChart,
      Reactive
    },
    data () {
      return {
        // instantiating datacollection with null
        datacollection: null
      }
    },
    created () {
      //anytime the vue instance is created, call the fillData() function.
      this.fillData()
    },
    methods: {
      fillData () {
        this.datacollection = {
          // Data for the y-axis of the chart
          labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'],
          datasets: [
            {
              label: 'Data One',
              backgroundColor: '#f87979',
              // Data for the x-axis of the chart
              data: [this.getRandomInt(), this.getRandomInt(), this.getRandomInt(), this.getRandomInt(), this.getRandomInt(), this.getRandomInt(), this.getRandomInt(), this.getRandomInt(), this.getRandomInt(), this.getRandomInt(), this.getRandomInt(), this.getRandomInt()]
            }
          ]
        }
      },
      getRandomInt () {
        // JS function to generate numbers to be used for the chart
        return Math.floor(Math.random() * (50 - 5 + 1)) + 5
      }
    }    
  }
</script>