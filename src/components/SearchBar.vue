<template>
  <div id="search">
    <form>
        <i class="fas fa-search"></i>
        <input type="text" placeholder="Search for a country">
    </form>
      
    <div class="dropdown">
        <button class="dropbtn"><span>Filter by Region</span> &nbsp;<i class="fas fa-angle-down"></i></button>
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
    width: 35%;
    background: #FFFFFF;
    margin-right: 20px;
    box-shadow: 0px 0px 6px lightgray;
    display: flex;
    align-items: center;
    padding: 0px 20px;
    border-radius: 5px;

    i{
        color: rgb(119, 119, 119);
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
    box-shadow: 0px 0px 6px lightgray;
    border-radius: 5px;

    button{
        background: #FFFFFF;
        padding: 15px 20px;
        width: 200px;
        display: flex;
        justify-content: space-between;
        align-items: center;
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
        border-radius: 5px;
        display: none;

        a{
            width: 100%;
            padding: 10px 20px;

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