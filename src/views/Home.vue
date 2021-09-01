<template>
  <div class="home">
    <Search-bar/>
    <section>
       <router-link to="/detail" v-for="n in 8" :key="n" class="card">
         <img id="flag" src="https://restcountries.eu/data/nga.svg" alt="">
         <ul id="details">
           <h1>Country Name</h1>
           <li>Population: 446, 734</li>
           <li>Region: Africa</li>
           <li>Capital: Abuja</li>
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
  }
}
</script>

<style scoped lang="scss">
section{
  margin-top: 50px;
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

    #flag{
      width: 100%;
    }

    ul{
      list-style: none;
      padding: 20px;

      h1{
        margin-bottom: 20px;
      }
    }
  }
}
</style>
