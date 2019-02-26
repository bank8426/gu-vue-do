<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>To do list</h2>
    <ul>
      <li v-if="doToList.length" v-for="(item, index) in doToList" :key="item.id">
        <label>{{index+1}}.{{item.description}}</label>
        <input type="checkbox" v-model="item.finish">
      </li>
    </ul>
    <div>
      <label>New item : </label>
      <br>
      <label>Description: </label>
      <input type="text" v-model="inputToDoObject.description">
      <label>Finish: </label>
      <input type="checkbox" v-model="inputToDoObject.finish">
      <button v-on:click="addItem(inputToDoObject)">Add</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      msg: 'Gu Vue Do',
      doToList: [],
      inputToDoObject: {
        description: '',
        finish: false
      }
    }
  },
  methods: {
    addItem: function (item) {
      console.log(item.description + ' ' + item.finish)
      console.log(this.doToList)
      this.doToList.push({description: item.description, finish: item.finish})
      item.description = ''
      item.finish = false
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
