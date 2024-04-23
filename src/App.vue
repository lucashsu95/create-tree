<script setup>
import { ref } from 'vue'
import ChildComp from './components/ChildComp.vue'

const ary = ref([['a','b'],['a','c'],['b','d'],['b','e']])
</script>

<template>
  <ChildComp title='a' :ary='ary' />
</template>
