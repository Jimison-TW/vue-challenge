<template>
  <div id="container">
    <div v-for="(symbol,key) in symbols" :key="key">
      <input type="button" class="calculate_button" @click="press(symbol)" :value="symbol">
    </div>
  </div>
</template>

<script>
export default {
  name: 'function_button',
  data: function() {
    return { symbols: ['+', '-', 'x', '/', 'CE', '='] }
  },
  methods: {
    press(symbol) {
      this.$emit('onCalculate', symbol)
    }
  }
}
</script>

<style>
#function_button {
  float: left;
}

.calculate_button {
  width: 40px;
  height: 40px;
}
</style>
