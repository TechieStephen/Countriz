<template>
  <div class="footer">
    <ul>
      <li>
        <a href="https://www.twitter.com/ohienstephen">
          <i class="fab fa-twitter-square"></i>
        </a>
      </li>
      <li>
        <a href="https://www.facebook.com/ohienstephen">
          <i class="fab fa-facebook-square"></i>
        </a>
      </li>
      <li>
        <a href="https://github.com/ohienstephen">
          <i class="fab fa-github-square"></i>
        </a>
      </li>
    </ul>
    <p>
      Challenge by 
      <a href="https://www.frontendmentor.io/">Frontend Mentor</a>. 
      Coded by <a href="https://ohienstephen.github.io/">Ohien Stephen</a>.
    </p>
  </div>
</template>

<script>
export default {
  name: 'Footer'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.footer{
  text-align: center;
  padding: 10px 5%;

  ul{
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 10px;

    li{
      padding: 5px;
      margin: 0px 10px;
      a{
        font-size: 16px;
        i{
          font-size: 30px;
        }
      }
    }
  }

  p{
    a{
      font-weight: bold;
    }
  }
}
</style>
