<template>
  <div class="home">
    <Search-bar/>

    <section>
       <div class="card">
       </div>
    </section>
  </div>
</template>

<script>
import SearchBar from '../components/SearchBar.vue'
// @ is an alias to /src
export default {
  name: 'Home',
  components: {
    SearchBar
  }
}
</script>


