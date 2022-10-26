<script setup>
import { ref, computed } from "vue";

const name = "Vue 3";

const counter = ref(0);

const arrayFavoritos = ref([])

const increment = () => counter.value++;

const decrement = () => counter.value--;

const reset = () => counter.value = 0;

const add = () => {
  arrayFavoritos.value.push(counter.value)
}

const bloquearBtnAdd = computed(() => {
  const numSearch = arrayFavoritos.value.find(num => num === counter.value)
  console.log(numSearch);
  if(numSearch === 0) return true;
  return numSearch ? true : false;
})

const classCounter = computed(() => {
  if(counter.value === 0) {
    return 'zero'
  }
  if(counter.value > 0) {
    return 'positive'
  }
  if(counter.value < 0) {
    return 'negative'
  }
})

</script>

<template>
  <div class="container text-center mt-3">
      <h1>Hola {{ name }}!</h1>
      <h2 :class="classCounter"> {{ counter }} </h2>
      <div class="btn-group">

        <button @click="increment" class="btn btn-success">Incremet</button>
        <button @click="decrement" class="btn btn-danger">Decrement</button>
        <button @click="reset" class="btn btn-secondary">Reset</button>
        <button @click="add" :disabled="bloquearBtnAdd" class="btn btn-primary">Add</button>

      </div>
  <ul class="list-group mt-4">
    <li class="list-group-item" v-for="(num, index) in arrayFavoritos" :key="index">
        {{num}}
      </li>
    </ul>

  </div>

    
</template>

<style>
.negative {
    color: red;
}

.positive {
    color: green;
}

.zero {
  color: peru;
}
</style>




<!-- <script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <TheWelcome />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style> -->
