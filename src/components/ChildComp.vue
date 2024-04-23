<script setup>
import { computed,ref } from 'vue'
  
const props = defineProps({
  title:String,
  ary: Array
})

const ary2 = ref(props.ary)
const ary3 = computed(()=>{
  const tmp = []
  console.log(ary2.value)
  for(const i of ary2.value){
    if(i[0] == props.title){
      tmp.push(i[1])
    }
  }
  return tmp
})
</script>

<template>
  
  {{title}}
  {{ary3}}
</template>