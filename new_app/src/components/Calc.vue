<template>
  <div class='hello'>
    <h1>{{ title }}</h1>
    <p>{{ message }}</p>
    <hr>
    <div>
      <div><textarea v-model='fomula' cols='40' rows='5' placeholder='計算式を入力'></textarea></div>
      <div><button @click='doAction'>CALC</button></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Calc',
  props: {
    title: String
  },
  data: function () {
    return {
      message: 'Enter expression',
      fomula: ''
    }
  },
  methods: {
    doAction: function () {
      let arr = this.fomula.trim().split('\n')
      let last = arr.pop()
      let fn = ''
      for (let n in arr) {
        if (arr[n].trim() != ''){
          fn += 'var ' + arr[n] + ';'
        }
      }
      fn += 'return '+ last + ';'
      let exp = 'function f() {' + fn + '} f();'
      let ans = eval(exp)
      this.message = 'answer: ' + ans
      let re = arr.join(';').trim();
      if (re != '') { re += ';'}
      re += last
      this.$emit('result-event', re, ans)
    }
  }
}
</script>

<style>
h1 {
  font-size: 3rem;
  color: #ccc;
}
p span {
  font-weight: bold;
  font-size: 2rem;
}
textarea {
  padding: 15px;
  border-radius: 3px;
  border: 1px solid #ccc;
  width: 30vw;
  font-size: 2rem;
  color: #333;
}
button {
  padding: 10px;
  width: 30vw;
  border-radius: 3px;
  background-color: #eee;
}
button:hover {
  background-color: #aaa;
}
</style>
