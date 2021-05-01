<script>
import { Bar } from 'vue-chartjs'
export default {
    extends: Bar,
    props: {
        label:{
            type:String
        },
        chartData:{
            type: Array
        },
         chartData2:{
            type: Array
        },
        options:{
            type:Object
            }
    },
    mounted() {
        const ranks = this.chartData.map(t=> t.rank);
        const market_cap_usd = this.chartData2.map(t=> t.market_cap_usd);

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

<style>
    .ticker{
        padding: 1rem;
        border: 1px dotted #ccc;
        margin: 1rem 0;
    }

</style>