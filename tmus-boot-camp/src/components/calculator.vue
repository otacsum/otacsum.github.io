<template>
  <div id="calculator">
    <h1>{{ msg }}</h1>
    <h3>Enter two integers:</h3>
    <input v-model.number="integerX" type="number" @keypress="onlyIntegers" placeholder="Enter an integer">
    <input v-model.number="integerY" type="number" @keypress="onlyIntegers" placeholder="Enter another integer">
    <button v-on:click="doMath">Let's do some math!</button>
    <p>{{ sumOfTwoInts }}</p>
    <p>{{ diffOfTwoInts }}</p>
    <p>{{ prodOfTwoInts }}</p>
    <p>{{ quotOfTwoInts }}</p>
    <p>{{ modOfTwoInts }}</p>
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
      sumOfTwoInts: '',
      diffOfTwoInts: '',
      prodOfTwoInts: '',
      quotOfTwoInts: '',
      modOfTwoInts: '',
      integerX: '',
      integerY: ''
    }
  },
  methods: {
    doMath() {
      //Calc sum
      this.getSum(this.integerX, this.integerY);
      //Calc difference
      this.getDifference(this.integerX, this.integerY);
      //Calc product
      this.getProduct(this.integerX, this.integerY);
      //Calc quotient
      this.getQuotient(this.integerX, this.integerY);
      //Calc modulus
      this.getModulus(this.integerX, this.integerY);
    },

    onlyIntegers($event) {
      //if keyCode returns, use it otherwise use the char code.  For x-browser support.
      let keyCode = ($event.keyCode ? $event.keyCode : $event.which);

      //Filter out decimals so only integers are returned.
      if (keyCode == 46) {
        $event.preventDefault();
      }
    },

    //Math functions broken out for readability.
    getSum(intX, intY) {
      var sum = intX + intY;
      this.sumOfTwoInts = "The sum of " + intX + " and " + intY + " is: " + sum;
    },
    getDifference(intX, intY) {
      var difference = intX - intY;
      this.diffOfTwoInts = "The difference of " + intX + " minus " + intY + " is: " + difference;
    },
    getProduct(intX, intY) {
      var product = intX * intY;
      this.prodOfTwoInts = "The product of " + intX + " times " + intY + " is: " + product;
    },
    getQuotient(intX, intY) {
      var quotient = intX / intY;
      this.quotOfTwoInts = "The quotient of " + intX + " divided by " + intY + " is: " + quotient;
    },
    getModulus(intX, intY) {
      var modulus = intX % intY;
      this.modOfTwoInts = "The modulus (remainder) of " + intX + " divided by " + intY + " is: " + modulus;
    }
  }
}
</script>\