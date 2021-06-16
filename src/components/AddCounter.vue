<template>
  <div class="container">
    <input
      type="number"
      v-model="inputNumber"
      @input="isValid"
      class="counter-input"
      placeholder="Enter your step value..."
      @keydown.enter="createCounter"
    />
    <button class="add-counter-btn" @click="createCounter">Add counter</button>
  </div>
</template>

<style scoped></style>
<script>
export default {
  emits: ["create-counter"],
  data() {
    return {
      inputNumber: null,
    };
  },
  methods: {
    isValid() {
      // Check the input for only one decimal
      this.inputNumber = this.inputNumber.match(/^-?\d+\.?\d{0,1}/);

      // Get the object made with RegEx and convert it into Number
      this.inputNumber = parseFloat(this.inputNumber[0]);
    },
    createCounter() {
      if (this.inputNumber == null) {
        // Alert if the input is empty
        alert("Enter a number!");
      } else {
        // Send the value to parent and make the input 0 again
        this.$emit("create-counter", this.inputNumber);
        this.inputNumber = 0;
      }
    },
  },
};
</script>

<style scoped>
.container {
  margin-top: 3rem;
  border: 1px solid #346751;
  border-top: 3px solid #346751;
  width: 60%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-radius: 5px;
  box-shadow: 0px 10px 15px -3px rgba(0, 0, 0, 0.1);
  background-color: #fff;
}
.counter-input {
  margin: 1rem;
  padding: 0.3rem;
  border: none;
  border: 1px solid #47a0c2;
  border-radius: 5px;
  width: 60%;
}
.counter-input:focus {
  outline: none;
  border: none;
  border: 2px solid #47a0c2;
}
.add-counter-btn {
  margin: 1rem;
  border: 1px solid #719dd8;
  cursor: pointer;
  width: 27%;
  height: 50%;
  background-color: transparent;
  border-radius: 50px;
  color: #000;
  transition: all 0.2s;
}
.add-counter-btn:hover {
  border: 1px solid #719dd8;
  background-color: #719dd8;
  color: #fff;
}
</style>
