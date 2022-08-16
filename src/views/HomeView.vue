

<template>
<main v-if="!loading">
<DataTitleVue :text="title" :dataDate="dataDate"/>
<DataBoxesVue :stats="stats"/>
<CountrySelectVue :countries="countries" @countryChanged="getCountryData"/>
</main>
<main v-else class="flex justify-center align-center flex-col text-center">
  <div class="text-gray-500 text-3xl mt-10 mb-6">
    Fetching Data
  </div>
  <img src="../assets/loading.gif" alt="Loading" class="w-24 m-auto">
</main>
</template>

<script>

import DataTitleVue from '../components/DataTitle.vue';
import DataBoxesVue from '../components/DataBoxes.vue';
import CountrySelectVue from '../components/CountrySelect.vue';
export default {
  name:'Home',
  components:{
    DataTitleVue,
    DataBoxesVue,
    CountrySelectVue
  },
  data(){
    return{
      loading:true,
      title:'Global',
      dataDate:'',
      stats:{},
      countries:[],
     
    }
  },
  methods:{
  async  fecthData(){
    const resp = await fetch('https://api.covid19api.com/summary');
    const data=await resp.json();
    return data;
  },
  getCountryData(country){
this.stats=country
this.title=country.Country
  }
  },
  async created(){
    const data= await this.fecthData();
    this.dataDate=data.Date,
    this.stats=data.Global,
    this.countries=data.Countries,
    this.loading=false,
console.log(data)

  }
}
</script>