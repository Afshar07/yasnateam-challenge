<template>
  <div class="container">
    <input
      type="number"
      v-model="inputNumber"
      @input="isValid"
      class="counter-input"
      placeholder="Enter your number"
    />
    <button class="add-counter">Add counter</button>
  </div>
</template>

<style scoped></style>
<script>
export default {
  data() {
    return {
      inputNumber: null,
    };
  },
  methods: {
    isValid() {
      this.inputNumber = this.inputNumber.match(/^-?\d+\.?\d{0,1}/);
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
