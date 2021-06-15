<template>
  <div class="container">
    <input type="number" v-model="inputNumber" @input="isValid" />
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
