<template>
  <div class="counter-container">
    <div class="counter-title">
      <h2 class="title">Step {{ this.index + 1 }}</h2>
    </div>
    <div class="value-container">
      <h2 class="current-value">{{ this.defaultValue }}</h2>
    </div>
    <div class="step-value-container">
      <p class="step-value">
        <span class="value-text">Value:</span> {{ this.stepValue }}
      </p>
    </div>
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
  border: 1px solid #346751;
  border-top: 3px solid #346751;
  display: flex;
  flex-direction: column;
  min-width: 20vw;
  box-shadow: 0px 10px 15px -3px rgba(0, 0, 0, 0.1);
  background-color: #fff;
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
  color: red;
}
.value-text {
  color: #000;
}
.add-button {
  width: 50%;
  height: 1.7rem;
  margin-bottom: 1rem;
  align-self: center;
  background-color: transparent;
  border: 1px solid #719dd8;
  border-radius: 20px;
  cursor: pointer;
  transition: all 0.2s;
}
.add-button:hover {
  background-color: #719dd8;
  color: #fff;
}
.value-container {
  margin-top: 1rem;
  width: 30%;
  height: 40%;
  align-self: center;
  display: flex;
  justify-content: center;
  align-items: center;
}
.current-value {
  text-align: center;
  font-weight: normal;
  color: rgb(189, 101, 0);
}
.step-value-container {
  text-align: center;
  margin: 1rem;
}
</style>
