<template>
  <div class='wrap'>
    <h1>{{ title }}</h1>
    <p>{{ message }}</p>
    <input type='text' v-model='input' />
    <button @click='doAction'>Click</button>
    <hr>
    <p>value: <input type='number' v-model='val'></p>
    <table>
      <tr>
        <th>add(+2):</th>
        <td>{{add}}</td>
      </tr>
      <tr>
        <th>sub(-2):</th>
        <td>{{sub}}</td>
      </tr>
      <tr>
        <th>multiple(*2):</th>
        <td>{{mult}}</td>
      </tr>
      <tr>
        <th>divide(/2):</th>
        <td>{{div}}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: 'BasicCalc',
  props: {
    title: String
  },
  data: () => {
    return {
      input: 'Name display',
      message: 'name input',
      val: 0,
      add: 0,
      sub: 0,
      mult: 0,
      div: 0,
    }
  },
  watch: {
    val: function (value) {
      this.val = value
      let val = parseInt(value)
      this.add = Math.floor(val + 2)
      this.sub = Math.floor(val - 2)
      this.mult = Math.floor(val * 2)
      this.div = Math.floor(val / 2)
    }
  },
  created: function () {
    this.val = 5
  },
  methods: {
    doAction: function () {
      this.message = 'こんにちは、' + this.input + 'さん！'
      this.$emit("result-event",this.input)
    }
  }

}
</script>

<style scoped>
.wrap {
  width: 80vw;
  margin: auto;
  padding: 0;
  text-align: center;
}
h1 {
  font-size: 12rem;
  font-weight: bold;
  letter-spacing: -1rem;
  line-height: 0.8;
  color: #8ad0a3;
  margin: 0;
}
p {
  margin: 0;
  color: #666;
  font-size: 4rem;
}
input {
  width: 10rem;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 3px;
  margin-bottom: 10px;
}
input[type=text] {
  border-radius: 3px 0 0 3px;
}
button {
  border-radius: 0 3px 3px 0;
  padding: 10px;
  border: 1px solid #ccc;
  border-left: none;
}
button:hover {
  background-color: #eee;
}
table {
  border-collapse: collapse;
  margin: auto;
}
th, td {
  border: 1px solid #ddd;
  padding: 10px;
}
tr:nth-child(even) {
  background-color: #efefef;
}
</style>

