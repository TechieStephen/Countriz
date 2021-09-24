<template>
  <div id="search">
    <form @submit.prevent="search">
        <i class="fas fa-search"></i>
        <input type="text" 
        placeholder="Search for a country" 
        v-model="name"
        v-on:keyup="search">
    </form>
      
    <div class="dropdown">
        <button class="dropbtn"><span>Filter by Region</span> &nbsp;<i class="fas fa-angle-down"></i></button>
        <div class="dropdown-content">
            <a href="#" v-on:click="$emit('searchByRegion', 'all')">All</a>
            <a href="#" v-on:click="$emit('searchByRegion', 'africa')">Africa</a>
            <a href="#" v-on:click="$emit('searchByRegion', 'Americas')">Americas</a>
            <a href="#" v-on:click="$emit('searchByRegion', 'asia')">Asia</a>
            <a href="#" v-on:click="$emit('searchByRegion', 'europe')">Europe</a>
            <a href="#" v-on:click="$emit('searchByRegion', 'oceania')">Oceania</a>
        </div>
    </div>
  </div>

</template>

<script>
export default {
 name:'SearchBar',
 data(){
     return{
         name:''
     }
 },
 methods:{
     search(){
         this.$emit('search', this.name)
     }
 }
}
</script>

<style scoped lang="scss">
#search{
 display: flex;
 justify-content: space-between;
 align-items: center;
}

form{
    width: 35%;
    margin-right: 20px;
    display: flex;
    align-items: center;
    padding: 0px 20px;
    border-radius: 5px;

    i{
        margin-right:5px;
    }

    input{
        flex: 1;
        padding: 15px;
        display: block;
    }
}

.dropdown{
    position: relative;
    font-weight: 600;
    font-size: 16px;
    border-radius: 5px;

    button{
        padding: 15px 20px;
        width: 200px;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }


    .dropdown-content{
        position: absolute;
        top:55px;
        display: flex;
        flex-direction: column;
        width: 100%;
        text-align: left;
        border-radius: 5px;
        display: none;

        a{
            width: 100%;
            padding: 10px 20px;
        }

    }

    &:hover .dropdown-content{
        display: flex;
    }
}

@media screen and (max-width:900px){
  #search{
    flex-direction: column;

    form{
        width: 100%;
        margin: 0 auto;
        margin-bottom: 15px;
    }

    .dropdown{
        width: 100%;
        margin: 0 auto;

        button{
        width: 100%;
    }
    }
}
}
</style>
