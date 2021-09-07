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
        <div>
          <router-link  to="/" v-for="(item,index) in borders" :key="index"> {{item}}, 
          </router-link>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name:'Detail',
  props:['code'],
  data(){
    return{
      country:{},
      borders:[]
    }
  },
  mounted(){
    fetch(`https://restcountries.eu/rest/v2/alpha/${this.code}`)
    .then(res=>res.json())
    .then(data=>{
      this.country = data
      this.country.borders.forEach(item => {
        this.borders.push(item)
      });
      console.log(data)
      console.log(this.borders)
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
  margin-top: 70px;
  display: flex;
  justify-content: space-between;
  align-items: center;

  #flag{
    width: 30%;
  }

  #country-details{
    width: 60%;

    h1{
      margin: 20px 0px;
    }
    #details{
      display: flex;
      justify-content: flex-start;
      margin: 20px 0px;

      ul:first-child{
        margin-right: 5%;
      }

      ul{
        font-size: 16px;
        li{
          margin: 8px 0px;
          span{
            font-weight: 600;
          }
        }
      }
    }

    #footer{
      margin-top: 40px;
      display: flex;
      align-items: center;

      h5{
        margin-right: 5%;
      }
      div{
        width: 50%;
        display: flex;
        align-items: center;
        justify-content: space-between;
        a{
          padding: 5px 30px;
          font-size: 15px;
        }
      }
    }
  }
}

@media (max-width:900px){
  section{
    flex-direction: column;
    #flag{
      width: 100%;
    }
    #country-details{
      width: 100%;
      #details{
        flex-direction: column;

          ul:first-child{
            margin-right: 0px;
            margin-bottom: 30px;
        }
      }

       #footer{
        flex-direction: column;
        align-items: flex-start;

        h5{
          margin: 15px 0px;
          width: 100%;
        }
        div{
          width: 100%;
          flex-wrap: wrap;

          a{
            margin-bottom: 10px;
          }
        }
      }
    }
  }
}
</style>
