<template>
  <div class="counter-container">
    <h2>Step {{ this.index + 1 }}</h2>
    <h2>{{ this.defaultValue }}</h2>
    <button @click.prevent="runCounter(this.stepValue)">RUN</button>
  </div>
</template>

<script>
export default {
  props: ["stepValue", "index"],
  data() {
    return {
      // Make the recieved number Float
      steps: parseFloat(this.stepValue),
      defaultValue: 0,
    };
  },

  methods: {
    runCounter(value) {
      // Make the current number & step value Float and add them to newestValue
      let newestValue = parseFloat(this.defaultValue) + parseFloat(value);

      // Check if the number is float or integer
      if (Number.isInteger(newestValue)) {
        this.defaultValue = newestValue;
      } else {
        // Change the decimals to only 1 number
        this.defaultValue = newestValue.toFixed(1);
      }
    },
  },
};
</script>
