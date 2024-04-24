<script setup>
import { computed, ref } from "vue";

const props = defineProps({
  title: String,
  ary: Array,
  direc: Number,
  childLen: Number,
});

const ary2 = ref(props.ary);
const ary3 = computed(() => {
  const tmp = [];
  console.log(ary2.value);
  for (const i of ary2.value) {
    if (i[0] == props.title) {
      tmp.push(i[1]);
    }
  }
  return tmp;
});
</script>

<template>
  <div class="boxs">
    <div
      class="box"
      :class="[
        { left: direc == 0},
        { right: direc == 1},
        { 'one-child': childLen == 1 },
      ]"
    >
      {{ title }}
    </div>
    <div class="childern">
      <ChildComp
        v-for="(tt, idx) in ary3"
        :key="tt"
        :title="tt"
        :ary="props.ary"
        :direc="idx"
        :childLen="ary3.length"
      ></ChildComp>
    </div>
  </div>
</template>

<style>
.boxs {
  display: flex;
  align-items: center;
  flex-direction: column;
}

.box {
  width: 50px;
  height: 50px;

  margin: 10px;
  font-size: 22px;
  border: 1px solid #aaa;
  border-radius: 50%;
  background: #000;

  display: flex;
  justify-content: center;
  align-items: center;

  position: relative;
}

.left::before,
.right::before,
.one-child::before {
  content: "";
  width: 2px;
  height: 20px;
  background: #ddd;
  border-radius: 4px;
  position: absolute;
  z-index: -1;
  top: -35%;
  left: 50%;
}

.left:not(.one-child)::before {
  transform: rotate(45deg) translate(-25%, -50%);
}

.right:not(.one-child)::before {
  transform: rotate(-45deg) translate(-25%, -50%);
}

.childern{
  display: grid;
  grid-template-columns: repeat(2,1fr);
}
</style>
