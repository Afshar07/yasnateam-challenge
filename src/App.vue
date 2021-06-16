<template>
  <div class="main-container">
    <div class="add-counter">
      <transition name="slide-in" appear>
        <add-counter @create-counter="createCounter"></add-counter>
      </transition>
    </div>
    <transition-group name="scale" tag="div" class="counters" appear>
      <counter-template
        v-for="(item, index) in counterSteps"
        :key="index"
        :index="index"
        :stepValue="item"
      ></counter-template>
    </transition-group>
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

<style>
body {
  margin: 0 !important;
  padding: 0 !important;
}
</style>
<style scoped>
.main-container {
  min-height: 100vh;
  background-color: #fff;
  width: 100%;
  display: flex;
  margin: auto;
  flex-direction: column;
  align-items: center !important;
  justify-content: center;
  background-color: #fff;
}
.add-counter {
  width: 100%;
  display: flex;
  justify-content: center;
}
.counters {
  display: flex;
  margin: auto;
  flex-wrap: wrap;
  justify-content: center;
}
.scale-enter-active {
  animation: bounce 0.5s;
}
.slide-in-enter-active {
  animation: slide 0.5s;
}

@keyframes bounce {
  0% {
    transform: translateY(-10vh);
  }
  7% {
    transform: translateY(-5vh);
  }
  10% {
    transform: translateY(-2vh);
  }
  15% {
    transform: translateY(0);
  }
  20% {
    transform: translateY(2vh);
  }
  30% {
    transform: translateY(4vh);
  }
  37% {
    transform: translateY(2vh);
  }
  45% {
    transform: translateY(0);
  }
  53% {
    transform: translateY(-2vh);
  }
  60% {
    transform: translateY(-4vh);
  }
  67% {
    transform: translateY(-2vh);
  }
  75% {
    transform: translateY(0);
  }
  90% {
    transform: translateY(2vh);
  }
  100% {
    transform: translateY(0);
  }
}
@keyframes slide {
  from {
    opacity: 0;
    transform: translateX(-30vw);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}
</style>
