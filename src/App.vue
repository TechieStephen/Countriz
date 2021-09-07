<template>
  <div id="wrapper" :class="{'dark':mode}">
    <Header @mode="changeMode"/>
    <main>
      <router-view/>
    </main>
    <Footer/>
  </div>
</template>

<script>
import Footer from './components/Footer.vue'
import Header from './components/Header.vue'
export default {
  components: { Header, Footer },
  data(){
    return{
      mode:false
    }
  },
  methods:{
    changeMode(){
      this.mode = !this.mode
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
  font-size: 1.1em;
}

#app {
  font-family: 'Nunito', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: $LightModeText;
  background: $LightModeBackground;
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

h1, h2{
  font-size: 1.2em;
}

main{
  padding: 50px 5%;
  min-height: 100vh;
}

//Light Mode Setup
.header,button, select, input, form, 
.dropdown, .dropdown-content, .card, #back, #flag, #footer a{
  background: #FFFFFF;
  color: $LightModeText;
}

.header, form, .dropdown, .dropdown-content, .card, #back, #flag, #footer a{
  box-shadow: 0px 0px 6px lightgray;
}

//Light Mode Setup
.dark{
  background: $DarkModeBackground;
  color: $DarkModeText;
  
  .header,button, button:active, select, input, 
  form, .dropdown, .dropdown-content, 
  .card, #back, #flag, #footer a{
    background: $DarkModeElements;
    box-shadow: none;
    color: $DarkModeText;
  }
  
  input:active, input:focus, input::placeholder{
    color: $DarkModeText;
  }
}

@media (max-width:900px){
  button, select, input{
    font-size: 16px;
  }
}
</style>
