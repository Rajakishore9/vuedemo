<template>
  <div>
    <!-- <FormView /> -->

    <AxioView />

  </div>
</template>

<script>

//import FormView from './components/FormView.vue'
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'
import AxioView from './components/axioView.vue'
export default {
  name: 'App',
  components: {
    //FormView,
    AxioView
  }
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
