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
      steps: parseFloat(this.stepValue),
      defaultValue: 0,
    };
  },

  methods: {
    runCounter(value) {
      let newestValue = parseFloat(this.defaultValue) + parseFloat(value);
      if (Number.isInteger(newestValue)) {
        this.defaultValue = newestValue;
      } else {
        this.defaultValue = newestValue.toFixed(1);
      }
    },
  },
};
</script>
