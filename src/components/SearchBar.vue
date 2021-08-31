<template>
  <div id="search">
    <form>
        <img src="" alt="">
        <input type="text" placeholder="Search for a country">
    </form>
      
    <div class="dropdown">
        <button class="dropbtn">Filter by Region <span>$</span></button>
        <div class="dropdown-content">
            <a href="#">Africa</a>
            <a href="#">Ameriaca</a>
            <a href="#">Asia</a>
            <a href="#">Europe</a>
            <a href="#">Oceania</a>
        </div>
    </div>
  </div>

</template>

<script>
export default {
 name:'SearchBar'
}
</script>

<style scoped lang="scss">
#search{
 display: flex;
 justify-content: space-between;
 align-items: center;
}

form{
    flex: 1;
    input{
        padding: 20px 15px;
        display: block;
        min-width: 40%;
        box-shadow: 0px 0px 6px lightgray;
        border-radius: 4px;
    }
}

.dropdown{
    position: relative;
    font-weight: 600;
    font-size: 16px;
    box-shadow: 0px 0px 6px lightgray;
    border-radius: 4px;

    button{
        background: #FFFFFF;
        padding: 15px 20px;
    }


    .dropdown-content{
        position: absolute;
        top:55px;
        background: #FFFFFF;
        display: flex;
        flex-direction: column;
        width: 100%;
        text-align: left;
        box-shadow: 0px 0px 6px lightgray;
        border-radius: 4px;

        display: none;

        a{
            width: 100%;
            padding: 8px 20px;

            &:hover{
                background:hsl(0, 0%, 98%) ;
            }
        }

    }

    &:hover .dropdown-content{
        display: flex;
    }
}
</style>