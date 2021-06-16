<template>
  <div class="container">
    <div class="inner-container">
      <input
        type="number"
        v-model="inputNumber"
        @input="isValid"
        class="counter-input"
        placeholder="Enter your step value..."
        @keydown.enter="createCounter"
        :class="{ inputInvalid: notValid }"
      />
      <button class="add-counter-btn" @click="createCounter">
        Add counter
      </button>
    </div>
    <transition name="fade-in" appear>
      <p class="not-valid" v-if="notValid">Please enter a number!</p>
    </transition>
  </div>
</template>

<style scoped></style>
<script>
export default {
  emits: ["create-counter"],
  data() {
    return {
      inputNumber: null,
      notValid: false,
    };
  },
  methods: {
    isValid() {
      // Remove the error if any number was typed into the input
      if (this.inputNumber) {
        this.notValid = false;
      }
      // Check the input for only one decimal
      this.inputNumber = this.inputNumber.match(/^-?\d+\.?\d{0,1}/);

      // Get the object made with RegEx and convert it into Number
      this.inputNumber = parseFloat(this.inputNumber[0]);
    },
    createCounter() {
      if (this.inputNumber == null) {
        // Alert if the input is empty
        this.notValid = true;
      } else {
        this.notValid = false;
        // Send the value to parent and make the input empty again
        this.$emit("create-counter", this.inputNumber);
        this.inputNumber = null;
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
  flex-direction: column;
  border-radius: 5px;
  box-shadow: 0px 10px 15px -3px rgba(0, 0, 0, 0.1);
  background-color: #fff;
  padding-bottom: 1rem;
}
.inner-container {
  margin: 1rem 1rem 0 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
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
.inputInvalid {
  border: 1px solid #e40000;
}
.inputInvalid:focus {
  border: 2px solid #e40000;
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

.not-valid {
  padding: 0.5rem 0 0.5rem 0;
  width: 30%;
  margin: 0 0 1rem 10rem;
  color: #fff;
  text-align: center;
  background-color: #b60000;
  border-radius: 20px;
}
.fade-in-enter-from {
  opacity: 0;
}
.fade-in-enter-to {
  opacity: 1;
}
.fade-in-enter-active {
  transition: all 0.4s ease-in;
}
.fade-in-leave-from {
  opacity: 1;
}
.fade-in-leave-to {
  opacity: 0;
}
.fade-in-leave-active {
  transition: all 0.3s ease-out;
}
</style>
