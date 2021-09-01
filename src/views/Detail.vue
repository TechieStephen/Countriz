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
          <li><b>Native Name:</b> {{country.population}}</li>
          <li><b>Population:</b> {{country.nativeName}}</li>
          <li><b>Region:</b> {{country.region}}</li>
          <li><b>Sub Region:</b> {{country.subregion}}</li>
          <li><b>Capital:</b> {{country.capital}}</li>
        </ul>
        <ul>
          <li><b>Top Level Domain:</b> {{country.topLevelDomain}}</li>
          <li><b>Currencies:</b> {{country.currencies}}</li>
          <li><b>Languages:</b> {{country.languages}}</li>
        </ul>
      </div>
      <div id="footer">
        <h3>Bordered Countries:</h3>
        <a href="" v-for="(item,index) in country.borders" :key="index">
          {{item}}
        </a>
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
      code:'co'
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
  background: #FFFFFF;
  padding: 15px 20px;
  font-weight: 600;
  font-size: 16px;
  box-shadow: 0px 0px 6px lightgray;
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
    box-shadow: 0px 0px 6px lightgray;
  }
  #country-details{
    width: 48%;

  #details{
    display: flex;
    justify-content: flex-start;
    margin: 20px 0px;

    ul:first-child{
      width: 40%;
      margin-right: 20px;
    }
  }

    #footer{
      margin-top: 40px;
      display: flex;
    }
  }

}
</style>
