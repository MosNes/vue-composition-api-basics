<template>
  <div class="home">
    <div>
      <button class="btn" @click="decreaseCounter">-</button>
      <span class="counter">{{ counter }}</span>
      <button class="btn" @click="increaseCounter">+</button>
    </div>
  </div>
</template>

<!-- OPTIONS API------------------------ -->
<!-- <script>
export default {

  data() {
    return {
      counter: 0,
    }
  },

  methods: {
    increaseCounter() {
      this.counter++;
    },
    decreaseCounter() {
      this.counter--;
    }
  },
}
</script> -->

<!-- COMPOSITION API WITH SETUP FUNCTION------------------------ -->
<!-- <script>
  import {ref} from 'vue';
  export default {
    setup() {
      const counter = ref(0);

      const increaseCounter = () => {
        counter.value++;
      }

      const decreaseCounter = () => {
        counter.value--;
      }

      return {
        counter,
        increaseCounter,
        decreaseCounter
      }
    }
  }
</script> -->

<!-- COMPOSITION API WITH SCRIPT SETUP PATTERN (RECOMMENDED)------------------------ -->
<script setup>
import { ref } from 'vue';

//all code for counter
const counter = ref(0);

const increaseCounter = () => {
  counter.value++;
}

const decreaseCounter = () => {
  counter.value--;
}
</script>

<style>
.home {
  text-align: center;
  padding: 20px;
}

.btn,
.counter {
  font-size: 40px;
  margin: 10px;
}
</style>