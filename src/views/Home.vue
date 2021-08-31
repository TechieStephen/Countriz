<template>
  <div class="home">
    <Search-bar/>
    <section>
       <div v-for="n in 8" :key="n" class="card">
         <img src="" alt="">
         <h1>Country Name</h1>
         <ul id="details">
           <li>Population: 446, 734</li>
           <li>Region: Africa</li>
           <li>Capital: Abuja</li>
         </ul>
       </div>
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
    height: 300px;
    background: #FFFFFF;
    box-shadow: 0px 0px 6px lightgray;
    border-radius: 10px;
    margin-bottom: 50px;
  }
}
</style>
