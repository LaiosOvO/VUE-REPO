<script setup>
import { ref, watch,reactive,onMounted  } from 'vue'

const llllll = ref(null);
const el = ref(null);
const domList111 = ref([]);
const dataList111 = ref( [
  111,
  222,
  333
] )

onMounted( ()=>{
  llllll.value.value = "hello ref";

  console.log(domList111.value);

} )





</script>

<template>

<div class="Chapter_11">
  <h1>模板引用</h1>
  <h2>访问模板引用</h2>
  <input ref="llllll" >


  <h2>v-for中的模板引用</h2>
  <ul>
    <li v-for="item in dataList111" ref="domList111" >
      {{ item }}
    </li>
  </ul>


  <h2>函数模板引用</h2>
  <input :ref="(el) => { el=llllll }">


</div>

</template>


<style scoped>

</style>
