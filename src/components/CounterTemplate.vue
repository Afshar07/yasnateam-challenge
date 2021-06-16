<template>
  <div class="counter-container">
    <div class="counter-title">
      <h2 class="title">Step {{ this.index + 1 }}</h2>
    </div>
      <p class="step-value">Value: {{ this.stepValue }}</p>
    <h2>{{ this.defaultValue }}</h2>
    <button @click.prevent="runCounter(this.stepValue)" class="add-button">
      RUN
    </button>
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
<style>
.counter-container {
  margin: 2rem 3rem 1rem 3rem;
  border-radius: 5px;
  border: 1px solid #08a878;
  border-top: 3px solid #08a878;
  display: flex;
  flex-direction: column;
  min-width: 20vw;
  box-shadow: 0px 10px 15px -3px rgba(0, 0, 0, 0.1);
}
.counter-title {
  display: flex;
  border-bottom: 1px solid #487468;
}
.title {
  padding: 0.6rem 0.5rem 0.5rem 0.3rem;
  margin: 0;
  font-size: 1rem;
  font-weight: normal;
  color: #005a3f;
}
.step-value {
  padding: 0.6rem 0.5rem 0.5rem 0.3rem;
  margin: 0;
  font-size: 0.85rem;
}
.add-button {
  width: 50%;
  height: 1.7rem;
  margin-bottom: 1rem;
  align-self: center;
  background-color: transparent;
  border: 1px solid #08a878;
  border-radius: 20px;
  cursor: pointer;
}
.add-button:hover {
  background-color: #08a878;
  color: #fff;
}
</style>
