<template>
  <div id="app">
    <KeyboardMultiSelect :raw-data="[1,2,3,4,5]" @selectChange="handleSelectChange">
      <div style="width: 10rem;height: 10rem;">1</div>
      <div style="width: 10rem;height: 10rem;">2</div>
      <div style="width: 10rem;height: 10rem;">3</div>
      <div style="width: 10rem;height: 10rem;">4</div>
      <div style="width: 10rem;height: 10rem;">5</div>
    </KeyboardMultiSelect>
  </div>
</template>

<script>
import KeyboardMultiSelect from "./lib/keyboardMultiSelect/KeyboardMultiSelect";
export default {
  name: 'app',
  components:{
    KeyboardMultiSelect
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  methods:{
    handleSelectChange(val){
      console.log('detected select change')
      console.log('now selected data is: '+val)
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
