<template>
  <div class="container">
      <div class="row mt-5" v-if="ranks.length>0" >
          <div class="col">
              <h2> Tickers</h2>
              <Ticker :chartData2 = "market_cap_usd" :chartData = "ranks" :options="chartOptions" label= "market_cap_usd"/>
          </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import Ticker from '../../components/Ticker';

export default {
    components: {
        Ticker
    },
    data(){
        return{
            tickers:[],
            ranks:[],
            market_cap_usd:[],
            chartOptions:{
                responsive:true,
                maintainAspectRatio:false,
                tooltips: {
                    backgroundColor: '#17BF62'
                },
            title: 
            {
                display: true,
                text: 'Market Cap USD',
                fontSize: 24,
                fontColor: '#6b7280'
            },
            }
        }
    },
   async created(){
      const config = {
          headers: {
              'Accept': 'application/json'
          }
      }   
    try{
        const res = await axios.get('https://api.coinlore.net/api/tickers/', config);

        res.data.data.slice(0,20).forEach(t=>{
            const {
                rank,
                market_cap_usd
            }= t;
            this.ranks.push({rank});
            this.market_cap_usd.push({market_cap_usd});
        })

    } catch(err)
    {console.log(err)}
   },
    head(){
        return{
            title: 'api content',
            meta: [{
                hid: 'discription',
                name: 'discription',
                content: ' testing api '
            }]
        }
    }
}
</script>

<style>

</style>
