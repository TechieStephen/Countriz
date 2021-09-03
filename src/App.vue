<template>
  <div id="wrapper" class="dark">
    <Header/>
    <main>
      <router-view/>
    </main>
  </div>
</template>

<script>
import Header from './components/Header.vue'
export default {
  components: { Header },
  data(){
    return{
      mode:false
    }
  }
}
</script>
<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Nunito:wght@300;600;800&display=swap');

$DarkModeElements: hsl(209, 23%, 22%); //Dark Mode Elements
$DarkModeText : hsl(0, 0%, 100%); //(Dark Mode Text & Light Mode Elements)
$DarkModeBackground : hsl(207, 26%, 17%); //(Dark Mode Background)

$LightModeBackground : hsl(0, 0%, 98%); //(Light Mode Background)
$LightModeText : hsl(200, 15%, 8%); //(Light Mode Text)

$DarkGray : hsl(0, 0%, 52%); //(Light Mode Input)

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
  color: $LightModeText;
  background: $LightModeBackground;
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
  color:inherit;
  background: inherit;
}
a{
  text-decoration: none;
  color: inherit;
}
img{
  width: 100%;
}
ul{
  list-style: none;
}
main{
  padding: 50px 5%;
}
.header,button, select, input, form, .dropdown, .dropdown-content, .card{
  box-shadow: 0px 0px 6px lightgray;
}

.dark{
  color: $DarkModeText;
  background: $DarkModeBackground;

  .header,button, select, input, form, .dropdown, .dropdown-content, .card{
    background: $DarkModeElements;
    box-shadow: none;
  }
}
</style>
