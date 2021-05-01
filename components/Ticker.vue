<script>
// Ticker page to display the Bar chart in which the data will be shown

import { Bar } from 'vue-chartjs'
export default {
    extends: Bar,
    //props that will be passed from the parent class
    props: {
        label:{
            type:String
        },
        //variable to save first set of data
        chartData:{
            type: Array
        },
        //variable to save second set of data
         chartData2:{
            type: Array
        },
        //barchar options
        options:{
            type:Object
            }
    },
    mounted() {
        //dividing the two dimentional array into a flat array for the data to be passed into the bar chart
        const ranks = this.chartData.map(t=> t.rank);
        const market_cap_usd = this.chartData2.map(t=> t.market_cap_usd);
    //rendering the barchart
    this.renderChart(
        {
        labels: ranks,
        datasets: [{
            label: this.label,
            data: market_cap_usd,
        }]
    },this.options);
    }
  };

</script>
