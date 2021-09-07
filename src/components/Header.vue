<template>
  <div class="header">
    <router-link to="/">
      <h1>Where in the world? {{mode}}</h1>
    </router-link>
    <button @click="$emit('mode')" type="button" id="btn-dark">
      <i :class="{'fas':!mode, 'far':mode}" class="fa-moon"></i> Dark Mode
    </button>
  </div>
</template>

<script>
export default {
  props:['mode'],
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

  button{
    user-select: none;
    font-size: 15px;
  }

}
</style>
