<template>
  <div class="home">
    <h2>{{ appTitle }}</h2>
    <h3>{{ counterData.title }}:</h3>
    <div>
      <button class="btn" @click="decreaseCounter(2)">--</button>
      <button class="btn" @click="decreaseCounter(1)">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button class="btn" @click="increaseCounter(1)">+</button>
      <button class="btn" @click="increaseCounter(2)">++</button>
    </div>
    <p>This counter is {{ oddOrEven }}</p>
    <div class="edit">
      <h4>Edit counter title:</h4>
      <input v-model="counterData.title" type="text">
    </div>
  </div>
</template>
<script setup>
import { computed, reactive, ref, watch } from 'vue';
// const counter = ref(0),
     // counterTitle = ref("My Counter");
const appTitle = "My amazing Counter app";
const counterData = reactive({
  count: 0,
  title: "My Counter"
});
const count = ref();
watch(() => counterData.count, (newCount) => {
  if (newCount === 20) {
    alert("Way to go!! You made it to 20!!")
  }
})
const oddOrEven = computed(()=> {
  if(counterData.count % 2 === 0) return "even"
  return "odd";
})

// methods
const increaseCounter = amount => {
  counterData.count += amount;
}
const decreaseCounter = amount => {
  counterData.count -= amount;
}
</script>
<style>
.home {
  text-align: center;
  padding: 20px;
}
.btn, .counter {
  font-size: 40px;
  margin: 10px;
}
.edit {
  margin-top: 60px;
}
</style>
