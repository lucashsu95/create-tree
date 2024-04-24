<script setup>
import { ref,computed } from 'vue'
import ChildComp from './components/ChildComp.vue'

const ary = ref([['a','b'],['a','c'],['b','d'],['b','e'],['c','f'],['e','g'],['e','z'],['z','x'],['x','u'],['x','y'],['f','t'],['f','q'],['q','w'],['w','s'],['c','o']])
//const ary = computed(()=>{
//  ary = JSON.parse(text.value);
//  return ary
//})

</script>

<template>
  <!-- <textarea v-model="text" cols='50' rows='3'></textarea> -->
  <ChildComp title='a' :ary='ary' />
</template>
