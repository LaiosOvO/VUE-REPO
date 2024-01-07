<script setup>

let awesome = false;
let type = 'B'
let ok = true;


</script>

<template>


  <div>

    
    <div class="Chapter_5" >
      <h1>条件渲染</h1>
      <button @click="awesome = !awesome" >Toggle</button>

      <h1 v-if="awesome">Vue is awesome!</h1>
      <h1 v-else>Oh no 😢</h1>
      
      <h1>v-else-if</h1>
      <div v-if="type === 'A'">
        A
      </div>
      <div v-else-if="type === 'B'">
        B
      </div>
      <div v-else-if="type === 'C'">
        C
      </div>
      <div v-else>
        Not A/B/C
      </div>

      
      <h1>用 template 标签 上的 v-if </h1>
      <template v-if="ok">
        <h5>Title</h5>
        <p>paragraph 1</p>
        <p>paragraph 2</p>
      </template>

      <h1 v-show="ok" > Hello! </h1>
    </div>


  </div>
</template>


<style scoped>

</style>
