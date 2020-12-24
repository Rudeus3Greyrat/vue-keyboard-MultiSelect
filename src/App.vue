<template>
  <div id="app">
    <KeyboardMultiSelect :raw-data="rawData">
      <div v-for="(item,index) in rawData">
        <span>index</span>
        <span>{{ item.name }}</span>
        <ul>
          <li v-for="(item,index) in item.children">
            {{ item }}
          </li>
        </ul>
      </div>
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
      msg: 'Welcome to Your Vue.js App',
      rawData: [{ index: 1, name: 'jack', children: ['a', 'b', 'c'] }, { index: 2, name: 'jack', children: ['a', 'b', 'c'] }, { index: 3, name: 'jack', children: ['a', 'b', 'c'] }, { index: 4, name: 'jack', children: ['a', 'b', 'c'] }, { index: 5, name: 'jack', children: ['a', 'b', 'c'] }, { index: 6, name: 'jack', children: ['a', 'b', 'c'] }]
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
