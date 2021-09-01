<template>
  <div class="home">
    <Search-bar/>
    <section>
       <router-link to="/detail" v-for="n in 8" :key="n" class="card">
         <img id="flag" src="https://restcountries.eu/data/nga.svg" alt="">
         <ul id="details">
           <h1>Country Name</h1>
           <li><b>Population:</b> 446, 734</li>
           <li><b>Region:</b> Africa</li>
           <li><b>Capital:</b> Abuja</li>
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
      console.log(data)
    })
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
