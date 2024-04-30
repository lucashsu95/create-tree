<script setup>
import { ref, computed } from "vue";
import ChildComp from "./components/ChildComp.vue";

const text = ref("[['a','b'],['a','c'],['b','d']]");
const ary = computed(() => {
  try {
    const array = JSON.parse(text.value.replace(/'/g, '"'));
    return array;
  } catch (e) {
    return null;
  }
});
</script>

<template>
  <textarea v-model="text" cols="50" rows="3"></textarea>

  <ChildComp v-if="ary" title="a" :ary="ary" />
</template>
