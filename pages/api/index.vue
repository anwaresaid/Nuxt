<template>
<!-- taking the data from the api and passing it to ticker component -->
  <div class="container">
      <!-- checking if the array have values  -->
      <div class="row mt-5" v-if="ranks.length>0" >
          <div class="col">
              <h2> Tickers</h2>
              <!-- passing values into Ticker component -->
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
            //cerating empty variables that will be used to store data
            tickers:[],
            ranks:[],
            market_cap_usd:[],
            //setting options for the barchar
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
    //setting config for api request
   async created(){
      const config = {
          headers: {
              'Accept': 'application/json'
          }
      }   
    try{
        //getting the data from the given api using axios
        const res = await axios.get('https://api.coinlore.net/api/tickers/', config);

        //taking the first 20 elements from the array and pushing them into ranks and market_cap_usd
        res.data.data.slice(0,20).forEach(t=>{
            const {
                rank,
                market_cap_usd
            }= t;
            this.ranks.push({rank});
            this.market_cap_usd.push({market_cap_usd});
        })
        //catching an error if existed
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
