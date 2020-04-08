<template>
  <div class="container">
    <span class="ans"> {{ ans || 0 }} </span>
    <button @click="clear">AC</button>
    <button @click="AddSign">+/-</button>
    <button @click="findPercentage">%</button>
    <button @click="divide" class="operator">/</button>
    <button @click="append('7')">7</button>
    <button @click="append('8')">8</button>
    <button @click="append('9')">9</button>
    <button @click="times" class="operator">X</button>
    <button @click="append('4')">4</button>
    <button @click="append('5')">5</button>
    <button @click="append('6')">6</button>
    <button @click="minus" class="operator">-</button>
    <button @click="append('1')">1</button>
    <button @click="append('2')">2</button>
    <button @click="append('3')">3</button>
    <button @click="add" class="operator">+</button>
    <button @click="append('0')" class="zero">0</button>
    <button @click="dot">.</button>
    <button @click="equals" class="operator">=</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      previous: null,
      ans: '',
      operator: null
    }
  }, 
  methods: {
    clear() {
      this.ans = ''
    },
    AddSign() {
      if (this.ans == '') {
        this.ans = '0'
      }
      this.ans.search('-') >= 0 ? this.ans = this.ans.substring(1, this.ans.length) : this.ans = `-${this.ans}`
    },
    findPercentage() {
      if (this.ans !== '') {
        const percent = `${parseFloat(this.ans) / 100}`
        this.ans = percent
      }
    },
    append(number) {
      this.ans === '' ? this.ans = number :
      this.ans =  `${this.ans}${number}`
    },
    dot() {
      if (this.ans.indexOf('.') === -1) {
        if (this.ans.length===0) {
          this.ans = '0'
        }
        this.append('.')
      }
    },
    times() {
      this.setPrevious()
      this.operator = (a, b) => a * b
    },
    minus() {
      this.setPrevious()
      this.operator = (a, b) => a - b
    },
    divide() {
      this.setPrevious()
      this.operator = (a, b) => a / b
    },
    add() {
      this.setPrevious()
      this.operator = (a, b) => a + b
    },
    equals() {
      if (this.operator !== null) {
        this.ans = `${
        this.operator(
          parseFloat(this.previous), 
          parseFloat(this.ans)
        )}`
        this.operator = null
        this.previous = null
      }
    },
    setPrevious() {
      this.previous = this.ans
      this.ans = ''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  width: 40%;
  margin: 0px auto;
  display:grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax('50px', auto);
}

@media (max-width: 768px) {
  .container {
    width: 100%
  }
}

.container button {
  cursor: pointer;
  font-size: 40px;
  border: 1px solid rgb(187, 185, 185);
  outline: none;
}

.ans {
  cursor: pointer;
  font-size: 40px;
  outline: none;
  background: #464444;
  color: whitesmoke;
  grid-column: 1/5;
  text-align: right;
  padding: 5px;
  border: 4px solid rgb(39, 39, 39);
}

.zero {
  grid-column: 1/3;
}

.operator {
  color: whitesmoke;
  background: orange;
}

</style>
