<template>
  <div class="header">
    <h1>Where in the world?</h1>
    <button type="button"><i class="far fa-moon"></i> Dark Mode</button>
  </div>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.header{
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #FFFFFF;
  padding: 20px 5%;
  box-shadow: 0px 6px 6px lightgray;

  button{
    background: inherit;
  }
}
</style>
