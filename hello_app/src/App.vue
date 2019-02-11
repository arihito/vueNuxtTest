<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld 
      :title="message"
      @result-event="doAction"/>
      <button @click="doPrompt">Popup</button>
      <p>{{ result }}</p>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  components: {
    HelloWorld
  },
  data: function () {
    return {
      message: "test",
      result: "no event"
    }
  },
  methods: {
    doPrompt: function () {
      let result = prompt("input please!")
      this.message = result
    },
    doAction: function(message) {
      this.result = "Result: " + message + "!" 
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button {
  border-radius: 3px;
  padding: 10px;
  border: 1px solid #ccc;
}
button:hover {
  background-color: #eee;
}
</style>
