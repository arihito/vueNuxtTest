<template>
  <div class='hello'>
    <h1>{{ title }}</h1>
    <p>{{ message }}</p>
    <input type='text' v-model='input' />
    <button @click='doAction'>Click</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    title: String
  },
  data: () => {
    return {
      input: 'Name display',
      message: 'name input'
    }
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
.hello {
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
input[type=text] {
  width: 10rem;
  border-radius: 3px 0 0 3px;
  padding: 10px;
  border: 1px solid #ccc;
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
</style>

