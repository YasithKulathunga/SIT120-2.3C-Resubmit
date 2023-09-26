<script setup>
import { ref } from 'vue'

const count = ref(0)

function increment() {
  count.value++
}
</script>

<template>
  <!--3. Reactivity Fundamentals [ref(), <script setup>]-->
  <h1>Reactivity Fundamentals</h1>
  <button class="button" @click="increment">
    {{ count }}
  </button>
</template>

<style>
    .button {
      background-color: #4CAF50; 
      border: none;
      border-radius: 30px;
      color: white;
      padding: 16px 32px;
      text-align: center;
      text-decoration: none;
      display: inline-block;
      font-size: 16px;
      margin: 4px 2px;
      transition-duration: 0.4s;
      cursor: pointer;
    }

</style>