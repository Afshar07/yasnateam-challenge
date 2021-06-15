<template>
  <div class="counter-container">
    <h2>Step {{ this.index + 1 }}</h2>
    <h2>{{ this.steps }}</h2>
    <button @click.prevent="runCounter(this.stepValue)">RUN</button>
  </div>
</template>

<script>
export default {
  props: ["stepValue", "index"],
  data() {
    return {
      steps: parseFloat(this.stepValue),
    };
  },
  methods: {
    runCounter(value) {
      this.steps = this.steps + parseFloat(value);
    },
  },
};
</script>
