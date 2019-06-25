<template>
  <div id="buttonContainer">
    <div class="buttonDiv" v-for="(value,key) in numbers" :key="key">
      <input type="button" class="number_button" @click="pressNumber(value)" :value="value">
    </div>
  </div>
</template>

<script>
export default {
  name: 'NumberPad',
  data: function() {
    return {
      numbers: [7, 8, 9, 4, 5, 6, 1, 2, 3, 0]
    }
  },
  methods: {
    pressNumber(value) {
      this.$emit('onNumberClick', value)
    }
  }
}
</script>

<style>
.number_button {
  width: 40px;
  height: 40px;
}
.buttonDiv {
  display: inline-block;
}
#buttonContainer {
  width: 150px;
  margin: 0px auto;
}
</style>
