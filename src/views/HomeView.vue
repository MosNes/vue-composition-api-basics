<template>
  <div class="home">

    <h3>{{ counterData.title }}:</h3>

    <div>
      <button class="btn" @click="decreaseCounter">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button class="btn" @click="increaseCounter">+</button>
    </div>

      <div class="edit">
        <h4>Edit Counter Title</h4>
        <input type="text" v-model="counterData.title">
      </div>
  </div>
</template>

<!-- COMPOSITION API WITH SCRIPT SETUP PATTERN (RECOMMENDED)------------------------ -->
<script setup>
import { ref, reactive } from 'vue';

//all code for counter
const counterData = reactive({
  count: 0,
  title: 'My Counter'
})

const increaseCounter = () => {
  counterData.count++;
}

const decreaseCounter = () => {
  counterData.count--;
}

</script>

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



<style>
.home {
  text-align: center;
  padding: 20px;
}

.btn,
.counter {
  font-size: 40px;
  margin: 10px;
},
.edit {
  margin-top: 60px;
}
</style>