<template>
  <router-link to="/" id="back"> <i class="fas fa-arrow-left"></i> Back</router-link>
  <section>
    <div id="flag">
      <img :src="country.flag" alt="">
    </div>
    <div id="country-details">
      <h1>{{country.name}}</h1>
      <div id="details">
        <ul>
          <li><span>Native Name:</span> {{country.nativeName}}</li>
          <li><span>Population:</span> {{country.population}}</li>
          <li><span>Region:</span> {{country.region}}</li>
          <li><span>Sub Region:</span> {{country.subregion}}</li>
          <li><span>Capital:</span> {{country.capital}}</li>
        </ul>
        <ul>
          <li>
            <span>Top Level Domain:</span>&nbsp;
            <template v-for="(item, index) in country.topLevelDomain" :key="index"> {{item}}</template>
          </li>

          <li>
            <span>Currencies:</span>&nbsp;
            <template v-for="(item, index) in country.currencies" :key="index"> {{item.name}}</template>
          </li>

          <li>
            <span>Languages:</span>&nbsp;
            <template v-for="(item, index) in country.languages" :key="index"> {{item.name}}, </template>
          </li>
        </ul>
      </div>

      <div id="footer">
        <h5>Bordered Countries:</h5>
          <router-link  to="/" v-for="(item,index) in country.borders" :key="index"> {{item}}, 
          </router-link>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name:'Detail',
  // props:['code'],
  data(){
    return{
      country:{},
      code:'be'
    }
  },
  mounted(){
    fetch(`https://restcountries.eu/rest/v2/alpha/${this.code}`)
    .then(res=>res.json())
    .then(data=>{
      this.country = data
      console.log(data)
    })
    .catch(error=>console.log(error))
  }
}
</script>

<style lang="scss" scoped>
#back{
  padding: 15px 20px;
  font-weight: 600;
  border-radius: 5px;
  text-align: center;
  vertical-align: center;

  i{
    margin-right: 15px;
  }
}

section{
  margin-top: 80px;
  display: flex;
  justify-content: space-between;
  align-items: center;

  #flag{
    width: 46%;
  }

  #country-details{
    width: 48%;

    #details{
      display: flex;
      justify-content: flex-start;
      margin: 20px 0px;

      ul:first-child{
        width: 50%;
        margin-right: 25px;
      }

      ul{
        font-size: 16px;
        li{
          margin: 5px 0px;
          span{
            font-weight: 600;
          }
        }
      }
    }

    #footer{
      margin-top: 40px;
      display: flex;
    }
  }

}
</style>
