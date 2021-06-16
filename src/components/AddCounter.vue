<template>
  <div class="container">
    <input
      type="number"
      v-model="inputNumber"
      @input="isValid"
      class="counter-input"
      placeholder="Enter your number"
      @keydown.enter="createCounter"
    />
    <button class="add-counter" @click="createCounter">Add counter</button>
  </div>
</template>

<style scoped></style>
<script>
export default {
  emits: ["create-counter"],
  data() {
    return {
      inputNumber: 0,
    };
  },
  methods: {
    isValid() {
      if (this.inputNumber.length == 0) {
        return;
      } else {
        // Check the input for only one decimal
        this.inputNumber = this.inputNumber.match(/^-?\d+\.?\d{0,1}/);

        // Get the object made with RegEx and convert it into Number
        this.inputNumber = parseFloat(this.inputNumber[0]);
      }
    },
    createCounter() {
      // Send the value to parent and make the input 0 again
      this.$emit("create-counter", this.inputNumber);
      this.inputNumber = 0;
    },
  },
};
</script>

<style scoped>
.counter-input {
  margin: 1rem;
  border: 1px solid #47a0c2;
}
.counter-input:focus {
  outline: none;
  border: none;
  border-bottom: 2px solid #47a0c2;
}
.counter-input {
  width: 40%;
}
</style>
