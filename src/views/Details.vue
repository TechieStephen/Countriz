<template>
  <router-link to="/" id="back"> <i class="fas fa-arrow-left"></i> Back</router-link>
  
  <Loading v-if="loading"/>
  <section v-else>
    <div id="flag">
      <img :src="country.flags[0] || country.flags[1]" alt="">
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
          <router-link :to="`/detail/${item.alpha2Code}`" v-for="(item,index) in borders" :key="index"> {{item.name}}</router-link>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import Loading from '../components/Loading.vue'
export default {
  name:'Detail',
  props:['code'],
  components:{Loading},
  data(){
    return{
      country:{},
      borders:[],
      loading: true
    }
  },
  watch:{
    code(){
        this.getCountryDetails()
    }
  },
  methods:{
    getCountryDetails(){
      this.loading = true
      fetch(`https://restcountries.com/v2/alpha/${this.code}`)
        .then(res=>res.json())
        .then(data=>{
          console.log(data)
          setTimeout(()=>{
            this.country = data
            this.getBorders()
            this.loading = false
          }, 100)
        })
        .catch(error=>console.log(error))
    },
    getBorders(){
      this.country.borders.forEach(item => {
        console.log(item)
        fetch(`https://restcountries.com/v2/alpha/${item}`)
          .then(res=>res.json())
          .then(data=>{
            this.borders.push(data)
          })
          .catch(error=>console.log(error))
      });
    }
  },
  created(){
    this.getCountryDetails()
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
      align-items: flex-start;

      h5{
        margin-right: 5%;
      }
      div{
        width: 70%;
        display: flex;
        flex-wrap: wrap;
        align-items: center;
        justify-content: flex-start;
        a{
          padding: 5px 15px;
          font-size: 15px;
          margin-right: 20px;
          margin-bottom: 10px;
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
        }
      }
    }
  }
}
</style>

/*CREATE TABLE students(
	id INT(11),
    name VARCHAR(20),
    class VARCHAR(20)
);

INSERT INTO students
VALUES(1,"stephen", "python")
*/

SELECT * FROM students
