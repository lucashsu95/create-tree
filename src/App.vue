<script setup>
import { ref } from "vue";
import ChildComp from "./components/ChildComp.vue";

const ary = ref([["a", "b"]]);
const add = () => {
  ary.value.push(["", ""]);
};
const remove = (idx) => {
  ary.value.splice(idx, 1);
};
</script>

<template>
  <section>
    {{ ary }}
    <table>
      <tr v-for="(t, idx) in ary">
        <td><input type="text" v-model="t[0]" /></td>
        <td><input type="text" v-model="t[1]" /></td>
        <td v-show="ary.length > 1">
          <button class="removeBtn" @click="remove(idx)">-</button>
        </td>
        <td v-show="idx == ary.length - 1">
          <button class="addBtn" @click="add()">+</button>
        </td>
      </tr>
    </table>
  </section>
  <section>
    <ChildComp v-if="ary" title="a" :ary="ary" />
    <div v-else>錯誤 請檢查格式有沒有錯誤</div>
  </section>
</template>

<style>
table {
  border-collapse: collapse;
  border: 1px solid #ddd;
}
th,
td {
  padding: 8px;
  text-align: left;
  border-bottom: 1px solid #ddd;
}
table input {
  width: 30px;
  font-size: 22px;
}
button {
  zoom: 1.5;
  cursor: pointer;
}
.removeBtn {
  border: 1px solid #ff4524;
  color: #ff4524;
  background: #0000;
  border-radius: 4px;
}
.addBtn {
  border: 1px solid #a7ff74;
  color: #a7ff74;
  background: #0000;
  border-radius: 4px;
}
</style>
