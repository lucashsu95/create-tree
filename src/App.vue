<script setup>
import { ref, computed } from "vue";
import ChildComp from "./components/ChildComp.vue";

const text = ref(
  "[['a','b'],['a','c'],['b','d'],['b','e'],['c','f'],['e','g'],['e','z'],['z','x'],['x','u'],['x','y'],['f','t'],['f','q'],['q','w'],['w','s'],['c','o']]"
);
const ary = computed(() => {
  const array = JSON.parse(text.value.replace(/'/g, '"'));
  return array;
});
</script>

<template>
  <textarea v-model="text" cols="50" rows="3"></textarea>
  <ChildComp title="a" :ary="ary" />
</template>
