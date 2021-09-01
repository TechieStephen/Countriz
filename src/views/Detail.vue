<template>
  <router-link to="/" id="back"> <i class="fas fa-arrow-left"></i> Back</router-link>
  <section>
    <div id="flag">
      <img src="https://restcountries.eu/data/nga.svg" alt="">
    </div>
    <div id="country-details">
      <h1>Country Name</h1>
      <div id="details">
        <ul>
          <li><b>Native Name:</b> 446, 734</li>
          <li><b>Population:</b> 446, 734</li>
          <li><b>Region:</b> Africa</li>
          <li><b>Sub Region:</b> Africa</li>
          <li><b>Capital:</b> Abuja</li>
        </ul>
        <ul>
          <li><b>Top Level Domain:</b> 446, 734</li>
          <li><b>Currencies:</b> Africa</li>
          <li><b>Languages:</b> Abuja</li>
        </ul>
      </div>
      <div id="footer">
        <h3>Bordered Countries:</h3>
        <a href="" v-for="n in 3" :key="n">France</a>
      </div>
    </div>
  </section>
</template>

<script>
export default {

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
    width: 46%;

  #details{
    display: flex;
    justify-content: flex-start;
    margin: 20px 0px;

    ul:first-child{
      margin-right: 15%;
    }
  }

    #footer{
      margin-top: 40px;
      display: flex;
    }
  }

}
</style>
