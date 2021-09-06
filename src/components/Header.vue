<template>
  <div class="header">
    <h1>Where in the world?</h1>
    <button @click="$emit('mode')" type="button" id="btn-dark">
      <i class="far fa-moon"></i> Dark Mode
    </button>
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
  padding: 20px 5%;

  h1{
    font-size: 1.2em;
  }

  button{
    user-select: none;
    font-size: .5em;
  }

}
</style>
