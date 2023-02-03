<template>
  <div class="home">
    <h2>{{ appTitle }}</h2>
    <h3>{{ counterData.title }}:</h3>

    <div>
      <v-progress-linear
        v-model="counterData.count"
        color="red"
        :max="counterData.maxValue"
        height="25"
        reverse
      ></v-progress-linear>
    </div>
    <div>
      <div>Set Max Value</div>
      <div>
        <input type="number" v-model="counterData.maxValue" class="text-center">
      </div>
    </div>
    <div>
      <button class="btn" @click="decreaseCounter(2)">-2</button>
      <button class="btn" @click="decreaseCounter(1)">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button class="btn" @click="increaseCounter(1)">+</button>
      <button class="btn" @click="increaseCounter(2)">+2</button>
    </div>

    <p>This counter is {{ oddOrEven }}</p>

    <div class="edit">
      <h4>Edit Counter Title</h4>
      <input type="text" v-model="counterData.title" v-auto-focus>
    </div>
  </div>
</template>

<!-- COMPOSITION API WITH SCRIPT SETUP PATTERN (RECOMMENDED)------------------------ -->
<script setup>

//imports
import { reactive, computed, watch, onMounted } from 'vue';
import { vAutoFocus } from '@/directives/vAutoFocus';

//counter non-reactive data
const appTitle = 'My Basic Counter App'

//do stuff related to app title
onMounted(() => {
  console.log('Do Stuff Related to app title');
});

//all reactive counter data as a reactive object
const counterData = reactive({
  count: 0,
  maxValue: 20,
  title: 'My Counter'
})

//Watchers for counter data
watch(() => counterData.count, (newCount, oldCount) => {
  if (newCount === 20) {
    alert('ITS NOW 20!!!!');
  }
})

//Counter Computed Properties
const oddOrEven = computed(() => {
  if (counterData.count % 2 === 0) {
    return 'Even';
  }
  return 'Odd';
})

// Counter methods
const increaseCounter = amount => {
  console.log(amount);
  counterData.count += amount;
}

const decreaseCounter = amount => {
  counterData.count -= amount;
}

// Hooks
onMounted(() => {
  console.log('Do Stuff Related to counter');
});


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
}

.edit {
  margin-top: 60px;
}
</style>