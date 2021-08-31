<template>
  <Header/>
  <main>
    <router-view/>
  </main>
</template>

<script>
import Header from './components/Header.vue'
export default {
  components: { Header },
}
</script>
<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Nunito:wght@300;600;800&display=swap');
$DarkBlue: hsl(209, 23%, 22%); //Dark Mode Elements
$VeryDarkBlue : hsl(207, 26%, 17%); //(Dark Mode Background)
$VeryDarkBlue : hsl(200, 15%, 8%); //(Light Mode Text)
$DarkGray : hsl(0, 0%, 52%); //(Light Mode Input)
$VeryLightGray : hsl(0, 0%, 98%); //(Light Mode Background)
$White : hsl(0, 0%, 100%); //(Dark Mode Text & Light Mode Elements)

*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: 'Nunito', sans-serif;
}
body{
  font-size: 16px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: $VeryLightGray;
  min-height: 100vh;
}
button{
  cursor: pointer;
}
button, select, input{
  outline: none;
  border: none;
  font-weight: 600;
  font-size: 16px;
  font-family: 'Nunito', sans-serif;
}
a{
  text-decoration: none;
  color: inherit;
}
main{
  padding: 30px 5%;
}
</style>
