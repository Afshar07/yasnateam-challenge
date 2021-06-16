<template>
  <div class="main-container">
    <add-counter @create-counter="createCounter"></add-counter>
    <counter-template
      v-for="(item, index) in counterSteps"
      :key="index"
      :index="index"
      :stepValue="item"
    ></counter-template>
  </div>
</template>

<script>
import AddCounter from "./components/AddCounter.vue";
import CounterTemplate from "./components/CounterTemplate.vue";
export default {
  components: { AddCounter, CounterTemplate },
  data() {
    return {
      counterSteps: [1, 3, -2.6],
    };
  },
  methods: {
    createCounter(value) {
      // Push the new declared value to create new counter
      this.counterSteps.push(value);
    },
  },
};
</script>

<style scoped>
.main-container {
  display: flex;
}
</style>
