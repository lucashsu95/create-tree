<script setup>
import { computed,ref } from 'vue'
  
const props = defineProps({
  title:String,
  ary: Array,
  direc:Number,
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
    <div>
    <div class='box' :class="[{left : direc == 0},{right:direc == 1}]">{{title}}{{direc}}</div>
        <div style='display:flex'>
            <ChildComp v-for='(tt,idx) in ary3' :key='tt' :title='tt' :ary='props.ary' :direc='idx'></ChildComp>
        </div>
    </div>
</template>

<style>
.box{
  width:50px;
  height:50px;

  margin:10px;
  font-size:22px;
  border:1px solid #aaa;
  border-radius:50%;

  display:flex;
  justify-content:center;
  align-items:center;
}
</style>