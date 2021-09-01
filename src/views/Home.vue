<template>
  <div class="home">
    <Search-bar/>
    <section>
       <router-link to="/detail" v-for="(item,index) in countries" :key="index" class="card">
         <img id="flag" :src="item.flag" alt="">
         <ul id="details">
           <h1>{{item.name}}</h1>
           <li><b>Population:</b> {{item.population}}</li>
           <li><b>Region:</b> {{item.region}}</li>
           <li><b>Capital:</b> {{item.capital}}</li>
         </ul>
       </router-link>
    </section>
  </div>
</template>

<script>
import SearchBar from '../components/SearchBar.vue'
// @ is an alias to /src
export default {
  name: 'Home',
  components: {
    SearchBar
  },
  data(){
    return{
      countries:[]
    }
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res=>res.json())
    .then(data=>{
      this.countries = data
    })
    .catch(error=>console.log(error))
  }
}
</script>

<style scoped lang="scss">
section{
  margin-top: 80px;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;

  .card{
    width:23%;
    min-height: 300px;
    background: #FFFFFF;
    box-shadow: 0px 0px 6px lightgray;
    border-radius: 10px;
    margin-bottom: 50px;
    text-align: left;

    ul{
      padding: 20px;
      h1{
        margin-bottom: 20px;
      }
    }
  }
}
</style>
