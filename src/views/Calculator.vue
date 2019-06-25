<template>
  <div class="about">
    <h1>This is an calculator page</h1>
    <p>{{result}}</p>
    <div style="display: inline">
      <NumberPad @onNumberClick="displayNum" />
      <FunctionPad @onCalculate="startCalculate"/>
    </div>
  </div>
</template>

<script>
import NumberPad from '@/components/NumberPad.vue'
import FunctionPad from '@/components/FunctionPad.vue'

export default {
  name: 'calculator',
  components: {
    NumberPad,
    FunctionPad
  },
  data: () => ({
    result: 0,
    firstNumber: 0,
    calculateSymbol: '',
    isNumberClick: true
  }),
  methods: {
    displayNum(num) {
      if (num === 0 && this.result === 0) return
      if (this.isNumberClick) {
        this.result = 0
        this.isNumberClick = false
      }
      this.result =
        typeof this.result === 'number' ? `${num}` : this.result + num
    },
    startCalculate(symbol) {
      console.log(symbol)
      if (this.result === 0) return
      if (symbol === 'CE') {
        this.clearAll()
      } else {
        this.result = this.caulateResult(this.result, symbol)
        this.isNumberClick = true
      }
    },
    clearAll() {
      this.result = 0
      this.firstNumber = 0
      this.caulateSymbol = ''
    },
    caulateResult(num, symbol) {
      switch (symbol) {
        case '+':
          this.firstNumber += Number(num)
          break
        case '-':
          this.firstNumber -= Number(num)
          break
        case '*':
          this.firstNumber *= Number(num)
          break
        case '/':
          this.firstNumber /= Number(num)
          break
        case '=':
          this.result = this.caulateResult(num, this.caulateSymbol)
          this.firstNumber = 0
          this.caulateSymbol = ''
          return this.result
        default:
          this.result = 'error'
          this.clearAll()
          break
      }
      this.caulateSymbol = symbol
      return this.firstNumber
    }
  }
}
</script>
