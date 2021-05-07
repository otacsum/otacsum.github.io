<template>
  <div id="calculator">
    <h1>{{ msg }}</h1>

    <h3>Enter two integers:</h3>
    <div id="inputForm">
      <input v-model.lazy.number="integerX" type="number" @keypress="onlyIntegers" placeholder="Enter an integer">
      <input v-model.number="integerY" type="number" @keypress="onlyIntegers" placeholder="Enter another integer">
    </div>

    <div id="results">
      <div>
        <span v-if="integerY && !integerX" class="left">Please enter the first integer.</span>
        <span v-else-if="integerX && integerY" class="left">The sum of {{integerX}} + {{integerY}} is:</span>
        <span v-else-if="integerX" class="left">The sum of {{integerX}} and...</span>
          <span v-if="integerX && integerY" class="right">{{ sumOfTwoInts }}</span>
          <span v-else class="right"></span>
      </div>

      <div>
        <span v-if="integerX && integerY" class="left">The difference of {{integerX}} - {{integerY}} is:</span>
        <span v-else-if="integerX" class="left">The difference of {{integerX}} minus...</span>
          <span v-if="integerX && integerY" class="right">{{ diffOfTwoInts }}</span>
          <span v-else class="right"></span>
      </div>

      <div>
        <span v-if="integerX && integerY" class="left">The product of {{integerX}} X {{integerY}} is:</span>
        <span v-else-if="integerX" class="left">The product of {{integerX}} times...</span>
          <span v-if="integerX && integerY" class="right">{{ prodOfTwoInts }}</span>
          <span v-else class="right"></span>
      </div>

      <div>
        <span v-if="integerX && integerY" class="left">The quotient of {{integerX}} / {{integerY}} is:</span>
        <span v-else-if="integerX" class="left">The quotient of {{integerX}} divided by...</span>
          <span v-if="integerX && integerY" class="right">{{ quotOfTwoInts }}</span>
          <span v-else class="right"></span>
      </div>

      <div>
        <span v-if="integerX && integerY" class="left">The modulo (remainder) of {{integerX}} % {{integerY}} is:</span>
        <span v-else-if="integerX" class="left">The modulo (remainder) of {{integerX}} divided by...</span>
          <span v-if="integerX && integerY" class="right">{{ modOfTwoInts }}</span>
          <span v-else class="right"></span>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  name: 'calculator',
  props: {
    msg: String
  },
  data() {
    return {
      integerX: '',
      integerY: ''
    }
  },

  computed: {
    sumOfTwoInts() {  //Addition
      return this.integerX + this.integerY;
    },
    diffOfTwoInts() {  //Subraction
      return this.integerX - this.integerY;
    },
    prodOfTwoInts() {  //Multiplication
      return this.integerX * this.integerY;
    },
    quotOfTwoInts() {  //Division
      return Math.round(this.integerX / this.integerY * 100) / 100
    },
    modOfTwoInts() {  //Modulo
      return this.integerX % this.integerY;
    }
  },

  methods: {
    onlyIntegers($event) {
      //if keyCode returns, use it otherwise use the char code.  For x-browser support.
      let keyCode = ($event.keyCode ? $event.keyCode : $event.which);

      //Filter out decimals so only integers are returned.
      if (keyCode == 46) {
        $event.preventDefault();
      }
    }
  }
}
</script>