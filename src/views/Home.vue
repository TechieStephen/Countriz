<template>
  <div class="home">
    <Search-bar v-on:searchByRegion="filterByRegion" v-on:search="search"/>
    <Loading v-if="loading"/>
    <section v-else>
       <router-link :to="`/details/${item.alpha2Code}`" v-for="item,index in countries" :key="index" class="card">
         <img id="flag" :src="item.flag" alt="">
         <ul>
           <h2>{{item.name}}</h2>
           <li><span>Population:</span> {{item.population}}</li>
           <li><span>Region:</span> {{item.region}}</li>
           <li><span>Capital:</span> {{item.capital}}</li>
         </ul>
       </router-link>
    </section>
  </div>
</template>

<script>
import Loading from '../components/Loading.vue'
import SearchBar from '../components/SearchBar.vue'
// @ is an alias to /src
export default {
  name: 'Home',
  components: {
    SearchBar,
    Loading
  },
  data(){
    return{
      countries:[],
      loading:true
    }
  },
  methods:{
    getAll(){
      fetch('https://restcountries.com/v2/all')
      .then(res=>res.json())
      .then(data=>{
        setTimeout(()=>{
          this.countries = data
          console.log(data)
          this.loading = false
        }, 100)
      })
      .catch(error=>console.log(error))
    },

    filterByRegion(region){
      this.loading = true
      if(region == "all"){
        this.getAll()
      }else{
        fetch(`https://restcountries.com/v2/continent/${region}`)
        .then(res=>res.json())
        .then(data=>{
          setTimeout(()=>{
            this.countries = data
            this.loading = false
          }, 100)
        })
        .catch(error=>console.log(error))
      }
    },

    search(name){
        this.loading = true
      if(name == ""){
        this.getAll()
      }else{
        fetch(`https://restcountries.com/v3/name/${name}`)
          .then(res=>res.json())
          .then(data=>{
              setTimeout(()=>{
                this.countries = data
                this.loading = false
            }, 100)
          })
        .catch(error=>console.log(error))
      }
      
    }
  },
  mounted(){
    this.getAll()
  }
}
</script>

<style scoped lang="scss">
section{
  margin-top: 70px;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;

  .card{
    width:23%;
    min-height: 300px;
    border-radius: 10px;
    margin-bottom: 50px;

    #flag{
      width: 100%;
      height: 200px;
    }
    ul{
      padding: 20px;
      h2{
        margin-bottom: 15px;
      }
      li{
        font-size: 16px;
        margin: 5px 0px;
        span{
          font-weight: 600;
        }
      }
    }
  }
}
@media screen and (max-width:1200px){
  section{
    margin-top: 40px;
    .card{
      width:30%;
    }
  }
}
@media screen and (max-width:900px){
  section{
    flex-direction: column;
    margin-top: 40px;
    .card{
      width:100%;
      margin: 0 auto;
      margin-bottom: 50px;

      #flag{
      width: 100%;
      height: auto;
    }
    }
  }
}
</style>
